Ready for review
Select text to add comments on the plan
[버그 #186] 원정 상대선택에서 같은 길드 유저 묶여 등장
Context
원정(Subdue) 상대 선택 화면에서 같은 길드 유저가 4~5명씩 묶여 등장하는 버그. 의도치 않은 동작으로, 다양한 길드의 상대가 고르게 나와야 한다.

원인 분석
매칭 흐름 (Guild.Competitors)
Guild.cs:281-350

GetChallengers(guildID, 5) → Redis에서 점수 근접한 5개 길드 랜덤 선택
5개 길드의 모든 멤버를 리스트에 수집 (최대 300명)
레벨 차이 오름차순 정렬
상위 5명 선택
버그 발생 지점
319줄의 정렬 비교에 버그가 있음:

members.Sort((A, B) => A[0].AsLong().CompareTo(B[1].AsLong()));
//                       ^^^^                      ^^^^
//                       레벨차이(index 0)           길드인덱스(index 1) ← 잘못됨!
B[1]은 길드 인덱스(0~4)인데, B[0](레벨 차이)과 비교해야 한다. 현재는 레벨 차이를 길드 인덱스와 비교하므로:

길드 인덱스 0인 길드의 멤버들은 B[1] = 0 → 비교값이 매우 작아 상위로 몰림
결과적으로 첫 번째로 가져온 길드의 멤버들이 상위에 집중 → 같은 길드 유저 4~5명 묶여 등장
추가 문제: 중복 체크 위치
322~346줄에서 중복 체크(check.Contains)를 하지만, count 상한이 이미 5로 고정되어 있어 중복 발생 시 5명 미만이 반환될 수 있음.

수정 방안
1. 정렬 비교 수정 (핵심)
// 변경 전
members.Sort((A, B) => A[0].AsLong().CompareTo(B[1].AsLong()));

// 변경 후
members.Sort((A, B) => A[0].AsLong().CompareTo(B[0].AsLong()));
2. 중복 시 5명 미달 방지 (선택)
// 변경 전
for (int i = -1, count = Math.Min(5, members.Count); ++i < count;)

// 변경 후: 중복 스킵 시에도 5명 채울 수 있도록
for (int i = -1; ++i < members.Count && challengers.Count < 5;)
영향도
유저 영향: 전체 (원정 이용 유저)
데이터 호환성: 변경 없음 (서버 로직만 수정)
롤백: 즉시 가능 (Lambda 재배포)
클라이언트 업데이트: 불필요 (서버만 수정)
수정 파일
파일	변경
Server/User/Guild.cs:319	정렬 비교 B[1] → B[0]
Server/User/Guild.cs:323	루프 조건 변경 (5명 보장)
검증
수정 후 dotnet build -c Release 빌드 확인
원정 상대 목록에서 다양한 길드의 유저가 나오는지 확인
5명이 정상적으로 반환되는지 확인
