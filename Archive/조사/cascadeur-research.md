# Cascadeur 조사 보고서
## AI 보조 키프레임 3D 캐릭터 애니메이션 소프트웨어

> **조사일**: 2026.04.16
> **최신 버전**: Cascadeur 2026.1 (2026년 4월 출시)
> **공식 사이트**: https://cascadeur.com

---

## 목차

1. [개요](#1-개요)
2. [핵심 기능](#2-핵심-기능)
3. [AI 기능 상세](#3-ai-기능-상세)
4. [워크플로우 및 파이프라인](#4-워크플로우-및-파이프라인)
5. [Unreal Engine 연동](#5-unreal-engine-연동)
6. [가격 정책](#6-가격-정책)
7. [장단점](#7-장단점)
8. [경쟁 도구 비교](#8-경쟁-도구-비교)
9. [버전 이력 및 최신 업데이트](#9-버전-이력-및-최신-업데이트)

---

## 1. 개요

### Cascadeur란?

Cascadeur는 **AI 보조 키프레임 애니메이션 소프트웨어**로, 물리 기반 도구와 AI를 활용하여 3D 캐릭터 애니메이션을 제작하는 전문 툴이다. 게임 개발, 모션 그래픽, VFX 작업을 위한 아티스트 친화적 대안으로 설계되었다.

**핵심 포지셔닝**: 모캡 추출 도구가 아니라 **키프레임 애니메이션 생성 도구**. 기성 애니메이션 라이브러리도 아니며, AI와 물리를 활용한 **커스텀 캐릭터 애니메이션 제작**에 특화.

### 개발사: Nekki

| 항목 | 내용 |
|------|------|
| 설립 | 2002년, Dmitry Terekhin |
| 본사 | 러시아 상트페테르부르크 |
| 대표작 | Shadow Fight 시리즈, Vector 파쿠르 게임 시리즈 |
| Cascadeur 개발 시작 | 2006년 (Eugene Dyabin, Nekki 내부 애니메이션 도구로 시작) |
| 독립 제품 전환 | 2019년 |
| 얼리 액세스 출시 | 2021년 4월 |
| 개발팀 규모 | 25~30명 |
| 추가 투자 | $1.5M |

**개발 동기**: Maya 등 기존 도구가 물리학(균형, 무게, 운동량)과 단절되어 있다는 문제 인식에서 출발.

### 지원 플랫폼

- Windows 10 (v1809+), Windows 11
- macOS 13.3+
- Ubuntu 20.04+ Linux
- Android (모바일 버전)

### 최소 시스템 요구사항

- 64비트 Intel/AMD 멀티코어 프로세서 (SSE4.1), macOS는 Apple ARM
- 2.4GHz 이상
- RAM 4GB
- NVIDIA GTX 550 Ti 이상 (OpenGL 3.3)

---

## 2. 핵심 기능

### 2-1. AutoPosing (AI 보조 포징)

- AI 기반 리깅 시스템으로, **소수의 관절만 조정하면 나머지 신체를 자동 배치**
- 인간 포즈의 학습된 데이터베이스 기반으로 균형과 자연스러운 정렬 유지
- 엉덩이, 목까지 포즈 예측에 포함
- **손가락 AutoPosing**: 손가락 위치 변경 시 전체 손을 자연스럽게 조정
- 2026.1에서 **4족 보행 동물**(고양이, 말 등) AutoPosing 개선

### 2-2. AutoPhysics (AI 보조 물리)

- 물리 기반 알고리즘으로 애니메이션을 분석하여 **물리적으로 정확한 버전 제안**
- **고스트 캐릭터**(유령)로 물리 보정 포즈를 표시하면서 원본 애니메이션 보존

**부가 기능:**
- Compensation motion (보상 모션)
- Smooth Rotation (부드러운 회전)
- Secondary motion (2차 모션)
- Restore Unbound (바인딩 해제 복원)
- Smooth Trajectory (부드러운 궤적)
- Separation of Motion (모션 분리)

**타임라인 색상 코딩:**

| 색상 | 의미 |
|------|------|
| 주황색 | 탄도 궤적 (지지점 없음) |
| 노란색 | 약한 구간 (지지점 적음) |
| 녹색 | 강한 구간 (지지점 많음) |
| 회색 | AutoPhysics 비활성 |

**고스트 캐릭터 색상:**

| 색상 | 의미 |
|------|------|
| 녹색 | 편차 미미 |
| 빨간색 | 물리적으로 불가능, 수동 조정 필요 |
| 파란색 | 변경 적용됨, 재계산 필요 |

### 2-3. FK/IK 전환 및 블렌딩

| 모드 | 설명 | 최적 용도 |
|------|------|-----------|
| **FK** (Forward Kinematics) | 부모→자식 영향 전파 | 회전 움직임 |
| **IK** (Inverse Kinematics) | 자식→부모 역방향 영향 | 표면 상호작용 (걷기, 달리기, 사다리) |
| **Global FK** | 부모 회전 상속 없이 아치형 보간 | 사지 아치 모션 |

- **한 클릭 전환**: Alt+쉼표 또는 Shift+F
- 베이크 없이 전환 가능
- 신체 부위별로 다른 키네마틱스 타입 혼합 사용 가능
- IK 키프레임: 글로벌 좌표 고정 / FK 키프레임: 부모 상대 로컬 좌표

### 2-4. 궤적 편집 (Trajectory Editing)

- 선택한 객체의 이동 경로를 시각적으로 표시
- 스페이싱 이해 및 수정에 활용
- **Trajectory Edit Mode**: 보간 프레임 이동으로 간격 조정
- **Trajectory Tangents**: 탄젠트 핸들 조작으로 추가 키프레임 없이 궤적 곡선 변경

### 2-5. 그래프 에디터 & 타임라인

- 애니메이션 커브 시각화 및 직접 편집
- **보간 타입**: Bezier, Linear, Fixed
- **Interval Edit Mode**: Copy Tools와 함께 애니메이션 블렌딩
- **Paste into interval**: 기존 애니메이션에 다양한 영향도로 적용

---

## 3. AI 기능 상세

### 3-1. AutoPosing 작동 원리

- **머신 러닝 기반**: 인간 포즈 데이터베이스에서 학습
- 사용자가 소수의 컨트롤러(관절)를 배치하면, AI가 나머지 신체 전체를 자연스러운 포즈로 완성
- 신체 균형과 물리적 타당성을 자동 유지
- **로컬 머신 러닝**으로 작동 (서버 전송 불필요)

### 3-2. AutoPhysics 작동 원리

- 물리 기반 알고리즘이 기존 애니메이션 분석
- **무게중심(Center of Mass)** 기반 물리 시뮬레이션
- 탄도 궤적 자동 계산 (점프 등)
- **Snap to Physics**: 물리 시뮬레이션에 맞춰 포즈 스냅
- **Freeze Physics**: 실시간 업데이트 일시 정지
- **Set Priority Frame**: 특정 프레임 포즈 잠금

**Point Controller 파라미터:**

| 파라미터 | 옵션/범위 |
|----------|-----------|
| Apply Type | Mutable / Local Fixed / Fixed |
| Keep Global Rotation | 0-100 |
| Keep Global Translation | 0-100 |
| Center of Mass | 연결 필수 |

### 3-3. AI 인비트위닝 (Inbetweening)

- **2025.1에서 도입**, 이후 대폭 개선
- 전통적 보간(linear, Bezier)과 달리, **머신 러닝으로 키 포즈 사이의 자연스러운 모션 시퀀스 생성**
- 타임라인 보간 시스템에 통합: 신체 부위별로 전통적 보간과 AI 인비트위닝 혼합 가능
- 2025.3에서 **무브먼트 스타일 선택** 기능 추가
- 물리 시뮬레이션(래그돌 포함)은 모든 보간/인비트위닝 평가 후 최종 프레임을 입력으로 사용

### 3-4. Root Motion Tool (2026.1 신규)

- **디퓨전 모델** 기술 기반
- 레퍼런스 애니메이션에서 움직임 시그니처를 분석하여 새로운 클립에 스타일 적용
- 키 포즈 사이를 자동 생성하면서 기존 애니메이션을 스타일 레퍼런스로 사용 가능

### 3-5. 전통적 키프레임 애니메이션과의 차이점

| 구분 | 전통 방식 | Cascadeur |
|------|-----------|-----------|
| 키프레임 | 모든 키프레임 수동 설정 | AI가 포즈 완성 및 프레임 간 모션 생성 보조 |
| 물리 | 아티스트 역량에 의존 | 리그에 물리 객체(강체) 포함, 자동 계산 |
| 균형/무게 | 수동 표현 | 물리 정보가 리그 자체에 내장, 실시간 반영 |
| 작업 시간 | 수일~수주 | 대폭 단축 |

---

## 4. 워크플로우 및 파이프라인

### 4-1. 지원 파일 포맷

| 방향 | 포맷 | 비고 |
|------|------|------|
| **Import** | FBX, Collada (DAE), GLB/GLTF/VRM, USD | - |
| **Export** | FBX, DAE, GLB/GLTF | 유료 플랜만 |
| **Export** | USD | 모든 플랜 |
| **Export** | CASC (자체 포맷) | 무료 플랜 포함 |

### 4-2. Blender 연동

- Blender가 지원하는 모든 포맷(FBX, DAE, GLB/GLTF, USD) 호환
- **FBX가 가장 권장** (문제 발생 가능성 최소)
- **Cascadeur Bridge for Blender**: 전용 연동 플러그인으로 워크플로우 간소화
- Blender는 종합 DCC 도구, Cascadeur는 캐릭터 애니메이션 전문 → 상호보완적

### 4-3. Unity 연동

- Unity는 **미터** 단위, Cascadeur는 **센티미터** 단위 (변환 필요)
- FBX 포맷으로 주고받기

### 4-4. 파이프라인 고려사항

- Cascadeur는 **캐릭터 애니메이션 전용** (모델링, 고급 리깅, 씬 어셈블리, 렌더링, 합성은 타 소프트웨어 필요)
- 리그/FBX 파이프라인 경험 없는 팀은 임포트/리타게팅에 시간 소요 가능
- **Quick Rigging Tool**: 리깅 자동화 (meshy.ai, Auto Rig Pro 템플릿 지원)
- **Animation Retargeting** 지원 (2024.1+)
- **Animation Unbaking**: 모캡 데이터 후처리 지원

---

## 5. Unreal Engine 연동

### 5-1. Live Link 플러그인 (2026.1 신규)

| 항목 | 내용 |
|------|------|
| 지원 버전 | UE 5.5 ~ 5.7 + Cascadeur 2026.1+ |
| 개발 배경 | Epic MegaGrant $50,000 지원 |
| 설치 | 수동 다운로드 후 UE 플러그인 폴더에 설치 |
| 설치 경로 | `C:\Program Files\Epic Games\UE_5.x\Engine\Plugins\Editor` |
| 향후 계획 | FAB 마켓플레이스 등록 예정 |

### 5-2. Live Link 작동 원리

- Cascadeur에서 UE5로 **애니메이션 시퀀스를 실시간 스트리밍**
- 관절 이름 기반 매칭: Cascadeur의 애니메이션 트랜스폼을 UE 내 스켈레톤 메시의 동일 이름 관절에 적용
- 수동 FBX 내보내기/가져오기 반복 불필요

### 5-3. 주의사항

- **관절 이름과 스켈레톤 계층 구조가 반드시 동일해야 함**
- 관절 이름 불일치 시 UE 내 관절 인식 실패
- 계층 구조 차이 시 예상치 못한 회전 오프셋 발생 가능

### 5-4. 기존 워크플로우 (Live Link 이전)

- FBX 포맷으로 내보내기 후 UE에서 임포트
- 측정 단위 동일 (둘 다 **센티미터**)

---

## 6. 가격 정책

| 플랜 | 월간 | 연간 | 핵심 사항 |
|------|------|------|-----------|
| **Free** | $0 | $0 | 비상업적 사용만, CASC 포맷만 내보내기, 전체 애니메이션 도구셋 포함 |
| **Indie** | $19 | $96 (58% 할인) | 연간 수입 $100K 미만 제한, FBX/DAE 내보내기, 1년 후 영구 라이선스 전환 |
| **Pro** | $49 | $396 (33% 할인) | 상업적 사용 무제한, 모든 내보내기 포맷, 애니메이션 리타게팅 |
| **Teams** | $49/유저 | $396/유저 | Pro 기능 + 시트 관리, 전용 Discord, 30분 온보딩 콜, 영구 라이선스 전환 없음 |
| **Education** | - | $49 | 교육자/기관 전용, 비상업적 사용, 모든 내보내기 포맷 |

> **참고**: 연간 구독은 1년 후 **영구 라이선스로 전환** (구독 기간 마지막 버전 영구 사용 가능, Teams 제외).

---

## 7. 장단점

### 장점

- AI 도구가 캐릭터 애니메이션 **진입 장벽을 크게 낮춤**
- 물리 기반 도구로 사실적인 무게, 운동량, 균형 **자동 반영**
- 전통적 방법 대비 **작업 시간 대폭 단축**
- Quick Rigging Tool로 리깅 세팅 시간 절감
- 기존 워크플로우에 **최소한의 학습 곡선**으로 통합 가능
- UE/Unity 내보내기 파이프라인 원활
- 무료 플랜 제공 (학습/비상업적 용도)
- 연간 구독 시 **영구 라이선스 전환** (1년 후)
- 모캡 데이터 후처리 (Unbaking) 가능

### 단점 / 제한사항

- **풀 DCC 스위트가 아님** (모델링, 고급 리깅 제작, 씬 어셈블리, 렌더링, 합성 미지원)
- 캐릭터 모션 전용, 범용 애니메이션 도구 아님
- 물리 우선 접근 방식이 전통 소프트웨어 사용자에게는 **학습 곡선 존재**
- 하이폴리 메시에서 성능 저하 가능
- 리그 준비 및 임포트 과정에서 트러블슈팅 필요할 수 있음
- 무료 플랜은 CASC 포맷만 내보내기 가능, 상업적 사용 불가
- **기성 애니메이션 라이브러리 미제공**

### 학습 곡선

| 수준 | 난이도 |
|------|--------|
| 기본 작업 | 매우 완만 |
| 고급 작업 | 리깅 워크플로우 및 물리 원리 이해 필요 시 가파름 |
| 전반적 | AI 도구 덕분에 전통 애니메이션 소프트웨어보다 접근성 높음 |

---

## 8. 경쟁 도구 비교

| 도구 | 유형 | 가격 | Cascadeur와의 차이점 |
|------|------|------|---------------------|
| **Blender** | 풀 DCC 스위트 | 무료/오픈소스 | 모델링/리깅/렌더링 포함, 애니메이션은 수동 키프레임 중심. Cascadeur와 **상호보완적** (Bridge 플러그인) |
| **Maya** | 풀 DCC 스위트 | ~$235/월 | 업계 표준, 종합 기능, AI 물리 보조 없음, 학습 곡선 높음 |
| **MotionBuilder** | 모캡 편집 전문 | 구독 (고가) | 모캡 편집/실시간 캐릭터 애니메이션 특화 |
| **Mixamo** | 애니메이션 라이브러리 | 무료 (Adobe) | 기성 모션 라이브러리 + 자동 리깅, 커스텀 애니메이션 생성 불가 |
| **DeepMotion** | 영상 기반 모캡 | 클라우드 SaaS | 영상→AI 모캡 데이터 생성. **모캡 추출** vs **키프레임 생성**의 근본적 차이 |
| **Plask** | 웹 기반 모캡 | 클라우드 SaaS | 웹캠/영상으로 모캡, 온라인 에디터, 인디 크리에이터 대상 |
| **RADiCAL** | AI 모캡 | 브라우저 기반 | 폰/영상으로 실시간 AI 모캡, 마커/수트 불필요 |
| **Move.ai** | AI 모캡 | 구독 기반 | 멀티 카메라 마커리스 모캡, 스튜디오 급 품질 |

### 포지셔닝 요약

```
[모캡 추출 도구]                    [키프레임 애니메이션 생성 도구]
DeepMotion, Plask,         vs      Cascadeur
RADiCAL, Move.ai

[범용 DCC 스위트]                   [캐릭터 애니메이션 전문]
Blender, Maya              vs      Cascadeur

[기성 라이브러리]                   [커스텀 제작]
Mixamo                     vs      Cascadeur
```

---

## 9. 버전 이력 및 최신 업데이트

### 주요 릴리스 타임라인

| 버전 | 시기 | 주요 기능 |
|------|------|-----------|
| 2024.1 | 2024.03 | 애니메이션 리타게팅, Unbaking 시스템 |
| 2024.2 | 2024 | 스윙 모션, Physics Corrector, Separation of Motion |
| 2024.3 | 2024 | 래그돌 물리, UE LiveLink (초기), 핫픽스 |
| 2025.1 | 2025.04 | AI 인비트위닝 도입 |
| 2025.2 | 2025.07 | AI 인비트위닝 대폭 개선, 모션 제어 옵션 |
| 2025.3 | 2025.11 | Filament 렌더 엔진 (실험적), 4족 보행 지원 (알파), 인비트위닝 통합 |
| **2026.1** | **2026.04** | Filament 정식, UE Live Link 재구축, Root Motion Tool, 충돌 클리닝, 4족 AutoPosing |

### Cascadeur 2026.1 핵심 신기능

1. **Filament 렌더링 엔진**: Google의 물리 기반 렌더 엔진 정식 채택, 뷰포트 품질 대폭 향상
2. **UE Live Link 재구축**: Cascadeur→UE5 실시간 애니메이션 스트리밍
3. **Root Motion Tool**: 디퓨전 모델 기반 AI 모션 스타일 전이
4. **Collision Penetration Cleaning**: 신체 교차/바닥 관통 자동 정리
5. **Constraints in AutoPhysics**: 무기/소품이 물리 시뮬레이션 중 캐릭터 손에 고정
6. **4족 AutoPosing 개선**: 고양이, 말 등 자연스러운 포징
7. **Quick Rigging Tool 템플릿**: meshy.ai, Auto Rig Pro 지원
8. **씬 조명 추가 기능**

---

## 참고 자료

- [Cascadeur 공식 사이트](https://cascadeur.com)
- [Cascadeur 2026.1 릴리스 블로그](https://cascadeur.com/blog/view/cascadeur-2026-1-new-renderer-ue-live-link)
- [Cascadeur 가격 정책](https://cascadeur.com/plans)
- [AutoPhysics 공식 문서](https://cascadeur.com/help/tools/physics_tools/autophysics)
- [Kinematics 공식 문서](https://cascadeur.com/help/animation_pipeline/spline/kinematics_in_cascadeur)
- [Live Link for UE 공식 문서](https://cascadeur.com/help/category/268)
- [Cascadeur for Blender Users](https://cascadeur.com/help/getting_started/for_other_software_users/cascadeur_for_blender_users)
- [CG Channel - Cascadeur 2026.1](https://www.cgchannel.com/2026/04/nekki-releases-cascadeur-2026-1/)
- [Digital Production - Cascadeur 2026.1](https://digitalproduction.com/2026/04/09/cascadeur-2026-1-adds-unreal-live-link-filament-rendering-and-ai-root-motion/)
- [Nekki 투자 정보 (WN Hub)](https://wnhub.io/news/investment/item-18739)
- [80.lv - Cascadeur Feature Dive](https://80.lv/articles/a-deep-dive-into-cascadeur-s-features)
