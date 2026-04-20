# 야구 선수 실제 영상 소스 확보 및 AI 모캡 파이프라인 조사
## 실사풍 야구 게임용 애니메이션 소스 확보 방법

> **조사일**: 2026.04.16
> **목적**: 야구 선수 실제 영상을 확보하여 AI 모캡으로 3D 애니메이션 데이터(FBX/BVH)를 추출하는 파이프라인 구축

---

## 목차

1. [영상 소스 확보 방법 (우선순위순)](#1-영상-소스-확보-방법)
2. [AI 영상 생성→모캡 파이프라인 (실험적)](#2-ai-영상-생성모캡-파이프라인)
3. [AI 모캡 도구별 영상 요구사항](#3-ai-모캡-도구별-영상-요구사항)
4. [법적/저작권 고려사항](#4-법적저작권-고려사항)
5. [추천 파이프라인](#5-추천-파이프라인)
6. [비용 비교](#6-비용-비교)

---

## 1. 영상 소스 확보 방법

### 1-1. DIY 촬영 (1순위 — 가장 추천)

가장 현실적이고 법적으로 안전한 방법. **완전한 상업적 권리를 확보**할 수 있다.

| 항목 | 내용 |
|------|------|
| **촬영 대상** | 대학/사회인 야구 선수 2~3명 고용 ($200~$1,000/일) |
| **촬영 장소** | 배팅 케이지, 실내 연습장 (깔끔한 단색 배경 확보) |
| **장비** | iPhone 12+ (4K/60fps 또는 1080p/240fps 슬로모션) × 2~3대 |
| **총 비용** | **$2,000 이하**로 수백 개 고유 동작 확보 가능 |
| **권리** | 촬영 동의서 받으면 완전한 상업적 권리 확보 |

**촬영 세팅 가이드:**

| 동작 | 프레임레이트 | 카메라 각도 | 비고 |
|------|-------------|-------------|------|
| **투구** | **240fps 필수** | 투수 측면 45도 | 팔 동작이 매우 빠름 (릴리즈 0.4초) |
| **타격** | **120fps 이상** | 타자 측면(수직) | 스윙 궤적 전체 캡처 |
| **수비** | 60fps 충분 | 정면 또는 측면 | 글러브 동작 포함 |
| **주루** | 60fps 충분 | 측면 | 가속/감속/슬라이딩 |

**촬영 팁:**
- 배경은 **단색벽 또는 단색 네트** 앞이 AI 모캡 정확도 극대화
- 카메라 거리: 피사체에서 **2~6m (6~20ft)**
- 카메라 높이: **가슴 높이** (고정, 삼각대 필수)
- 의상: **타이트한 옷** 권장 (헐렁한 유니폼은 관절 인식 저하)
- **줌/팬/컷 금지** — 고정 촬영만 유효
- 동일 동작을 3~5회 반복 촬영 → 최적 테이크 선택
- 가능하면 **3개 각도**(측면, 정면, 45도)로 동일 동작 촬영 → Move.ai Multi-Cam 활용 가능

**장비별 비교:**

| 장비 | 해상도/FPS | 장점 | 단점 |
|------|-----------|------|------|
| **iPhone 12+** | 4K/60fps, 1080p/240fps | AI 모캡 도구와 최적 호환, Move.ai 직접 지원 | 실내 저조도에서 노이즈 |
| **GoPro HERO11+** | 4K/120fps | 넓은 화각, 고FPS | 실내 조명 부족 시 화질 저하 |
| **Sony RX0 II** | 1080p/120fps | Move.ai 공식 지원 카메라 | 가격 높음 |

### 1-2. 무료 스톡 영상 (2순위)

| 사이트 | 콘텐츠 | 상업적 사용 | 모캡 적합도 | URL |
|--------|--------|-------------|-------------|-----|
| **Pexels** | 야구 영상 ~5,800개 | 무료, 저작권표시 불필요 | 연습/배팅 케이지 영상 일부 사용 가능 | https://www.pexels.com/search/videos/baseball/ |
| **Pixabay** | 야구 영상 34개+ | 무료 (Pixabay License) | 소량이지만 일부 사용 가능 | https://pixabay.com/videos/search/baseball/ |

**주의**: 무료 스톡 영상은 촬영 각도, 해상도, 프레임레이트가 AI 모캡에 최적화되어 있지 않은 경우가 많다. 프로토타이핑 용도로는 괜찮지만 프로덕션 품질을 기대하기 어렵다.

### 1-3. 유료 스톡 영상 (3순위)

| 플랫폼 | 가격 | 품질 | 게임 개발 라이선스 | 비고 |
|--------|------|------|-------------------|------|
| **Artgrid** | $49.92/월 (무제한 다운로드) | 4K/8K/RAW/LOG | **명시적으로 "games, animations, software" 포함** | 가성비 최고, 스포츠 카테고리 풍부 |
| **Pond5** | 클립당 $5~$500 | HD/4K/RAW | 표준 라이선스로 대부분 커버 | 기여자 가격, 개별 구매 |
| **Storyblocks** | $15~$30/월 (연간) | HD/4K | 구독 라이선스 | 스포츠 카테고리 보유 |
| **Shutterstock** | 커스텀 가격 | HD/4K | Extended License 필요 | MLB 관련 클립 ~1,586개 |
| **Getty Images** | 프리미엄 가격 | HD/4K | 별도 권리 패키지 | MLB 관련 클립 ~9,075개 |

**추천**: **Artgrid** — 무제한 다운로드 + 게임 개발 라이선스 명시 + 고품질 4K/8K 소스.

### 1-4. 기성 애니메이션 팩 (4순위 — 영상 대신 완성품)

영상 소스가 아닌 **이미 완성된 모캡 애니메이션 데이터**를 구매하는 방법.

| 제품 | 플랫폼 | 내용 | 가격 |
|------|--------|------|------|
| **POLYGONCRAFT Baseball Core Motions** | Unity Asset Store | 투수/포수/타자 핵심 동작 | ~$54 |
| **POLYGONCRAFT Baseball Extra Motions** | Unity Asset Store | 확장 동작 세트 | ~$55 |
| **Basic Baseball Movement** | Fab (UE) | UE용 야구 애니메이션 | 변동 |
| **MoCap Online Sports Packs** | FBX/BVH/UE/Unity | 2,500+ 애니메이션, 30+ 테마 팩 | 팩당 과금 |
| **MoCap Central** | FBX/BVH/UE/Unity | UE5/MetaHuman, Unity 파일 포함 | 팩당 과금 |

참고: https://mocaponline.com/ / https://mocapcentral.com/

### 1-5. 학술/연구 데이터 (5순위 — 참고용)

| 소스 | 내용 | 데이터 형식 | 라이선스 |
|------|------|------------|----------|
| **OpenBiomechanics** (Driveline Baseball) | 투수 100명 + 타자 98명의 전신 3D 마커 데이터 | C3D + CSV (키네마틱스/키네틱스/에너제틱스) | 비상업 무료 (CC BY-NC-SA 4.0), **상업용은 Driveline에 별도 라이선스 필요** |
| **CMU MoCap Database** | 2,605 모션, 140+ 피험자 (야구 특화는 적음) | BVH, C3D | **상업 사용 가능** (매우 관대) |
| **AMASS** | 40시간 모캡, 344 피험자 (CMU 포함, 야구 특화 적음) | SMPL/SMPL-X (NPZ) | 연구용, 상업용은 MPI에 문의 |

**OpenBiomechanics 상세:**
- GitHub: https://github.com/drivelineresearch/openbiomechanics
- 공식: https://www.openbiomechanics.org/
- 투수: 47개 신체 마커 + 22개 하지/골반 + 25개 상체 마커
- 타자: 47개 신체 마커 + 배트 마커
- **주의**: NonCommercial 조항으로 상업 게임에 직접 사용 불가. 상업 라이선스 별도 협의 필요.

---

## 2. AI 영상 생성→모캡 파이프라인 (실험적)

### 2-1. 개념

```
AI 영상 생성 (Sora/Runway/Kling/Veo)
        ↓  야구 선수 투구/타격 영상
영상→모캡 추출 (Move.ai/DeepMotion/Plask)
        ↓  FBX/BVH 스켈레톤 데이터
UE 5.7 임포트
```

### 2-2. AI 영상 생성 도구 현황 (2026년 기준)

| 도구 | 해상도 | 길이 | 스포츠 모션 품질 |
|------|--------|------|-----------------|
| **Sora** (OpenAI) | 최대 1080p | ~20~60초 | 비주얼은 인상적이나 생체역학적으로 부정확 |
| **Runway Gen-4** | HD | ~10초 | 빠른 운동 동작에서 블러 아티팩트 |
| **Kling 2.0** (Kuaishou) | HD/4K | ~2분 | 걷기/달리기는 양호, 빠른 스포츠 동작은 불안정 |
| **Veo 3** (Google) | 최대 4K | 가변 | 모션 리얼리즘 경쟁력 있으나 스포츠 특화 없음 |
| **Pika, MiniMax, Luma** | HD | 짧음 | 모캡 소스로 부적합 |

### 2-3. 현재 한계점

| 문제 | 설명 |
|------|------|
| **오류 복합** | AI 영상의 잘못된 역학 → 모캡이 그 오류를 충실히 추출 → 이중 오류 |
| **프레임레이트** | AI 영상은 대부분 24fps, 야구 투구는 **60fps 이상 필요** |
| **신체 일관성** | 프레임 간 팔다리 길이 변동, 관절 비정상 굽힘 |
| **물리 위반** | 팔이 몸을 관통하거나 관성을 무시하는 팔로우스루 |
| **Ground Truth 부재** | 실제 촬영은 물리적 현실이 있지만, AI 영상은 "환각"을 캡처하는 것 |
| **제어 불가** | "3/4 arm slot 4심 패스트볼" 같은 세밀한 프롬프트 제어 불가능 |

### 2-4. 결론

**프로토타이핑/기획 단계**: 동작 방향성 확인용으로는 사용 가능
**프로덕션 품질**: 현재 불가. **1~3년 후** 실용 수준 도달 예상
**출시된 게임 사례**: AI 생성 영상을 모션 소스로 사용한 상업 게임 **없음**

---

## 3. AI 모캡 도구별 영상 요구사항

### 3-1. DeepMotion (Animate 3D)

| 파라미터 | 요구사항 |
|----------|----------|
| 해상도 | 최소 1080p |
| 프레임레이트 | 최소 30fps, 60fps 권장 (프리미엄) |
| 카메라 거리 | 2~6m (6~20ft) |
| 카메라 위치 | 고정, 피사체 수직, 가슴 높이 |
| 신체 가시성 | 머리~발끝 전신, 끊김 없이 |
| 의상 | 타이트한 옷, 패턴/텍스처 권장 |
| 조명 | 중립적 균일 조명, 강한 그림자 없이 |
| 배경 | 피사체와 고대비 |
| 카메라 움직임 | 없음 (줌, 팬, 컷 금지) |

참고: https://www.deepmotion.com/article/single-person-capture-guidelines-for-animate-3d

### 3-2. Plask

| 파라미터 | 요구사항 |
|----------|----------|
| 해상도 | 최소 720p |
| 포맷 | MP4 또는 WebM |
| 파일 크기 | 최대 100MB |
| 길이 | 3초 ~ 5분 |
| 방향 | 가로 (세로는 인식 불량) |
| 신체 가시성 | 전신, 사지 잘림 없이 |
| 카메라 | 고정, 정면 시점 |
| 다인원 | 최대 10명, 겹침 없이, 1,800프레임 / 1분 이하 |

참고: https://plask.ai/en-US/docs/44

### 3-3. Move.ai

| 파라미터 | 요구사항 |
|----------|----------|
| 최대 해상도 | 4K |
| 최대 프레임레이트 | 120fps |
| 지원 카메라 | iPhone 8+, iPad 2019+, GoPro 7+, Sony RX0 II, 시네마 카메라 |
| Move One (싱글 카메라) | 1인 트래킹 |
| Move Pro (멀티 카메라) | 최대 12대 카메라, 20+ 인원 트래킹 |
| 가격 | $50/월 (1,200 크레딧) 또는 $365/년 (1,800 크레딧/월) |
| 크레딧 | 1 크레딧 = 1초 × 1인 |

참고: https://docs.move.ai/knowledge/move-ai-pricing-plans-credits

### 3-4. 야구 동작별 최적 촬영 설정

| 동작 | 최적 FPS | 최적 카메라 각도 | 이유 |
|------|---------|-----------------|------|
| **투구** | **240fps** (iPhone 슬로모션) | 투수 측면 45도 | 릴리즈 구간 팔 속도 70mph+, 블러 방지 |
| **타격** | **120fps** | 타자 측면(수직) | 스윙 궤적 + 체중 이동 캡처 |
| **수비** | 60fps | 정면 또는 측면 | 상대적으로 느린 동작 |
| **주루** | 60fps | 측면 | 가속/감속/슬라이딩 |
| **포수** | 120fps | 정면 또는 측면 45도 | 프레이밍 + 송구 동작 |

---

## 4. 법적/저작권 고려사항

### 4-1. 절대 하면 안 되는 것

| 소스 | 이유 |
|------|------|
| **MLB/KBO/NPB 방송 영상** | 상업적 사용 금지. AI 모캡 추출도 **파생 저작물**로 간주될 가능성 높음 |
| **유명 선수 특유의 동작 복제** | **퍼블리시티권(Right of Publicity)** 침해 |
| **MLB Film Room / Baseball Savant 영상 다운로드** | 이용약관 위반 + 상업적 사용 불가 |
| **경기장에서 촬영한 영상** | MLB은 관람 티켓으로는 상업적 촬영 권리를 부여하지 않음 |

### 4-2. 퍼블리시티권 판례

**Keller v. EA** 및 **Hart v. EA** 판례:
- 법원은 선수의 스포츠 동작을 사실적으로 묘사하는 것이 **"변형적(transformative)"이지 않다**고 판결
- 이름/얼굴을 사용하지 않더라도, 동작이 특정 선수를 **식별 가능**할 정도로 독특하면 퍼블리시티권 위반 가능
- **안전한 접근**: 유명하지 않은 선수의 일반적 동작 사용, 또는 직접 고용한 퍼포머의 동작 캡처

### 4-3. Fair Use 분석 (MLB 방송 영상 기준)

| 요소 | 판단 |
|------|------|
| 사용 목적/성격 | 상업적 게임 개발 → **불리** |
| 원저작물의 성격 | 창작적 방송 제작물 → **강하게 보호** |
| 사용 분량 | 짧은 클립도 "핵심"에 해당 → **불리** |
| 시장 영향 | 야구 게임은 MLB 라이선스 게임과 직접 경쟁 → **불리** |

**결론**: Fair Use 주장은 **극히 어려움**.

### 4-4. 상업 야구 게임에 필요한 라이선스

| 시나리오 | 필요 라이선스 |
|----------|-------------|
| **실제 선수 없이** (오리지널 캐릭터) | MLB/MLBPA 라이선스 불필요. 다만 팀명, 로고, 구장 사용 불가. **직접 촬영한 모캡 데이터만 필요** |
| **실제 선수 포함** | MLB 라이선스 (팀명, 로고, 구장) + MLBPA 라이선스 (선수 이름, 초상) 필요 — 비용 수백만 달러 |
| **스톡 영상 기반 모캡** | 스톡 라이선스에 "derivative works" + "software/games" 포함 확인 필요 |

### 4-5. MLB The Show는 어떻게 하는가?

- Sony Interactive Entertainment가 MLB + MLBPA **독점 라이선스 계약** 보유
- 전문 광학 모캡 스튜디오에서 120~240fps로 촬영 (Vicon, OptiTrack)
- 실제 프로 선수 + 전문 운동 퍼포머 고용
- 릴리스 사이클당 **수천 개 애니메이션** 캡처
- **모든 모션이 오리지널 캡처** — 방송 영상 추출이 아님

---

## 5. 추천 파이프라인

### 5-1. 최적 파이프라인 (인디 개발자 기준)

```
대학/사회인 야구 선수 2~3명 고용 + 배팅 케이지/연습장 촬영
  iPhone 2~3대: 4K/60fps + 1080p/240fps 슬로모션
  촬영 동의서(Commercial Release) 확보
        ↓
Move.ai (Multi-Cam) 또는 DeepMotion으로 AI 모캡 추출
        ↓  FBX 출력
Cascadeur 클린업
  - AutoPhysics: 물리적 정확도 보정
  - Foot Lock: 발 미끄러짐 제거
  - AI Inbetweening: 키프레임 간 보간
        ↓
AI 모션 변형 (1개 동작 → 수십 개 변형)
  - Cascadeur Root Motion Tool (디퓨전 기반 스타일 전이)
  - 체형별/타이밍별/좌우 미러링
        ↓
UE 5.7 임포트
  - Animation Sequence
  - Motion Matching으로 런타임 블렌딩
```

### 5-2. 용도별 소스 전략

| 용도 | 추천 소스 | 이유 |
|------|-----------|------|
| **핵심 게임플레이** (투구/타격/수비) | **DIY 촬영 + AI 모캡** | 정확도 최우선, 완전한 권리 |
| **보조 애니메이션** (세레머니, 걷기, 대기) | **무료 스톡 영상 + AI 모캡** 또는 **기성 팩** | 정확도 요구 낮음 |
| **프로토타이핑/기획** | **AI 영상 생성 + 모캡** 또는 **Text-to-Motion** | 방향성 확인용 |
| **모션 다양성 확보** | **핵심 모캡 세트 + AI 스타일 전이** | 가장 효율적인 AI 활용 |

---

## 6. 비용 비교

| 방법 | 총 비용 | 확보 가능한 동작 수 | 품질 | 법적 안전성 |
|------|---------|-------------------|------|------------|
| **DIY 촬영 + AI 모캡** | ~$2,000 | 수백 개 | 높음 | 완전 |
| **무료 스톡 + AI 모캡** | $0 | 수십 개 (적합 영상 제한적) | 중 | 완전 |
| **Artgrid 구독 + AI 모캡** | ~$50/월 | 수백 개 | 중~높음 | 완전 (라이선스 명시) |
| **기성 애니메이션 팩** | $50~$500 | 수십~수백 개 | 높음 (전문 모캡) | 완전 |
| **OpenBiomechanics 상업 라이선스** | 협의 필요 | 198명 분량 | 최고 (연구급) | 라이선스 협의 후 |
| **전문 모캡 스튜디오** | $10,000~$50,000+/일 | 수천 개 | 최고 | 완전 |
| **MLB 방송 영상 추출** | - | - | 중 | **불법 위험** |

### 최종 추천

**예산 $2,000 이하 인디 개발자**:
1. DIY 촬영 (핵심 동작 100~200개 확보)
2. Pexels/Pixabay 무료 스톡 (보조 동작 보충)
3. POLYGONCRAFT 팩 (~$110, 기본 동작 즉시 사용)
4. Cascadeur Root Motion Tool로 모션 변형 대량 생산
5. 총 **500개 이상의 야구 애니메이션** 확보 가능

---

## 참고 자료

### 영상 소스
- [MLB Film Room](https://www.mlb.com/video) — 참고용만, 상업 사용 불가
- [Baseball Savant](https://baseballsavant.mlb.com/) — 참고용만, 상업 사용 불가
- [Pexels Baseball Videos](https://www.pexels.com/search/videos/baseball/) — 무료 상업 사용
- [Pixabay Baseball Videos](https://pixabay.com/videos/search/baseball/) — 무료 상업 사용
- [Artgrid](https://artgrid.io/) — 유료, 게임 라이선스 명시
- [Pond5](https://www.pond5.com/search?kw=baseball&media=footage) — 유료 개별 구매

### AI 모캡 도구
- [Move.ai](https://www.move.ai/) — 싱글/멀티 카메라 AI 모캡
- [DeepMotion Animate 3D](https://www.deepmotion.com/) — 웹 기반 AI 모캡
- [Plask](https://plask.ai/) — 브라우저 기반 AI 모캡
- [Rokoko Video](https://www.rokoko.com/) — 무료 AI 모캡 + 클린업

### 애니메이션 마켓플레이스
- [MoCap Online](https://mocaponline.com/) — 스포츠 모캡 팩
- [MoCap Central](https://mocapcentral.com/) — UE5/MetaHuman 호환
- [POLYGONCRAFT (Unity)](https://assetstore.unity.com/publishers/10113) — 야구 특화 애니메이션

### 학술 데이터
- [OpenBiomechanics Project](https://www.openbiomechanics.org/) — 투수/타자 C3D 데이터
- [OpenBiomechanics GitHub](https://github.com/drivelineresearch/openbiomechanics)
- [CMU MoCap Database](https://mocap.cs.cmu.edu/) — 상업 사용 가능

### 법률/라이선스
- [MLB Terms of Use](https://www.mlb.com/official-information/terms-of-use)
- [NCAA Footage Policy](https://www.ncaa.com/_flysystem/public-s3/files/Footage%20Usage%20Licensing_1.pdf)
- [Right of Publicity in Video Games (Game Developer)](https://www.gamedeveloper.com/business/right-of-publicity-in-video-games)
- [Sports Motion Capture Guide (MoCap Online)](https://mocaponline.com/blogs/mocap-news/sports-motion-capture-guide)
