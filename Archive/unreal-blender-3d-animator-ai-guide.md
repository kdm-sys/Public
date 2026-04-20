# 🎬 3D 애니메이터를 위한 AI 활용 종합 가이드
## 실사풍 야구 게임 제작을 위한 최신 AI 도구 활용법 (Blender + Unreal Engine 5.7)

> **대상**: 3D 애니메이터 (Blender 사용, 실사풍 야구 게임 제작)  
> **프로젝트**: 야구매니저 (UE 5.7 기반)  
> **버전**: 1.0 (2026.04)  
> **작성**: CEO 미니

---

## 목차

1. [개요: 2026년 AI 애니메이션 지형도](#1-개요-2026년-ai-애니메이션-지형도)
2. [모션 캡처 — AI가 카메라 한 대로 끝낸다](#2-모션-캡처--ai가-카메라-한-대로-끝낸다)
3. [AI 키프레임 도구 — Cascadeur](#3-ai-키프레임-도구--cascadeur)
4. [Blender 워크플로우 가속화](#4-blender-워크플로우-가속화)
5. [AI 3D 모델 생성 + 자동 리깅](#5-ai-3d-모델-생성--자동-리깅)
6. [Unreal Engine 5.7 애니메이션 신기능](#6-unreal-engine-57-애니메이션-신기능)
7. [페이셜 애니메이션과 립싱크](#7-페이셜-애니메이션과-립싱크)
8. [클로스 / 헤어 / 근육 시뮬레이션](#8-클로스--헤어--근육-시뮬레이션)
9. [생성형 AI 텍스트→애니메이션](#9-생성형-ai-텍스트애니메이션)
10. [야구 게임 특화 워크플로우](#10-야구-게임-특화-워크플로우)
11. [Blender ↔ UE 5.7 파이프라인 최적화](#11-blender--ue-57-파이프라인-최적화)
12. [추천 도입 로드맵 (3개월)](#12-추천-도입-로드맵-3개월)
13. [비용 비교 및 ROI](#13-비용-비교-및-roi)
14. [레퍼런스](#14-레퍼런스)

---

## 1. 개요: 2026년 AI 애니메이션 지형도

### 패러다임 전환

전통적인 3D 애니메이션 파이프라인은 다음과 같이 구성되어 있었습니다:

```
컨셉 → 모델링 → 리깅 → 스키닝 → 키프레임 애니메이션 → 클린업 → 엔진 임포트
       (수일)   (수일)   (수일)    (수일~수주)        (수일)    (수일)
```

**2026년 AI 도구를 활용한 파이프라인:**

```
컨셉 → AI 3D 생성/모션캡처 → 자동 리깅 → AI 키프레임 보조 → 클린업 → 엔진 자동 임포트
       (수분~수시간)         (수분)      (수십분)         (수시간)  (수분)
```

전체 시간이 **5~10배 단축**되며, 1인 애니메이터가 과거 4-5명 팀의 산출물을 낼 수 있습니다.

### AI 도구를 어떻게 분류해야 하는가

3D 애니메이터 관점에서 AI 도구는 4개 영역으로 나뉩니다:

| 영역 | 역할 | 대표 도구 |
|---|---|---|
| **입력 생성** | 모션 데이터를 만들어 주는 도구 | Move AI, Cascadeur, SayMotion, KinaTrax |
| **에셋 생성** | 캐릭터/소품 모델/리그를 만드는 도구 | Tripo, Meshy, Hyper3D Rodin, Auto-Rig Pro AI |
| **워크플로우 자동화** | Blender/UE 안에서 반복 작업 자동화 | Blender MCP, BlenQuick, 3D-Agent |
| **엔진 통합** | 런타임에서 애니메이션을 동적으로 생성 | UE5 Motion Matching, ML Deformer, MetaHuman Animator |

야구 게임 같은 **실사풍 + 반복적 동작이 많은 게임**은 위 4개 영역 모두에서 AI 활용도가 매우 높습니다. 투구/타격/수비는 동작 패턴이 정형화되어 있어 모션 캡처와 모션 매칭에 최적이며, 선수 캐릭터는 다수가 필요해 자동 리깅과 ML Deformer가 유용합니다.

### 야구 게임에 특히 중요한 AI 도구의 가치

실사풍 3D 야구 게임은 아래 특성이 있습니다:

- **수백 개의 미세하게 다른 동작** (투구 폼만 수백 가지, 스윙 변형 수십 가지)
- **정확한 신체 메카닉** (실제 선수 동작 재현, 부상 위험 동작 회피)
- **클로스/헤어 시뮬레이션** (유니폼 펄럭임, 모자 떨어짐 등)
- **실시간 페이셜 애니메이션** (관중 반응, 선수 표정)
- **대량의 캐릭터 변형** (선수 신체/얼굴/유니폼 다양성)

이 모든 영역에서 2026년 현재 AI 도구가 실용적 수준에 도달했습니다.

---

## 2. 모션 캡처 — AI가 카메라 한 대로 끝낸다

### 2-1. AI 모션 캡처 도구 비교 (2026년 기준)

| 도구 | 카메라 | 가격 | 정확도 | 특징 |
|---|---|---|---|---|
| **Move AI (Move One)** | iPhone 1대 | $30/월~ | ★★★★★ | 단일 카메라 최고 정확도, Gen 2 모델 (s2) |
| **Move AI (Multi-Cam)** | iPhone 2-6대 | $365/년~ | ★★★★★★ | AAA 스튜디오급 품질, 손가락까지 캡처 |
| **DeepMotion Animate 3D** | 일반 비디오 | $15/월~ | ★★★★ | 웹 기반, SayMotion과 연동 |
| **Rokoko Vision** | 웹캠 1-2대 | 무료 (15초) | ★★★ | 무료 진입점, Plus $22/월 |
| **Plask Motion** | 웹캠/비디오 | $24/월~ | ★★★ | 가벼운 프로토타이핑 |
| **RADiCAL** | 비디오 | 종료 예정 | - | 2026년 7월 6일 서비스 종료 (Autodesk 인수) |
| **KinaTrax** | 멀티 카메라 | 엔터프라이즈 | ★★★★★★ | 야구 특화, MLB 구장 설치 |
| **Uplift** | iPad 2대 | 엔터프라이즈 | ★★★★★ | MLB/NBA/NCAA 50+ 팀 사용, 야구 특화 |

### 2-2. 야구 게임에 추천하는 조합

**프로토타이핑 단계** (혼자 빠르게 동작 만들기):
- **Move One** (iPhone 1대)
- 자기가 직접 투구/스윙 → iPhone으로 촬영 → 1분 내 FBX 추출
- 월 $30 수준으로 무제한에 가까운 시도 가능

**프로덕션 단계** (정확한 선수 동작 캡처):
- **Move Multi-Cam** (iPhone 4-6대)
- 야구장에서 실제 선수 촬영
- 수트 없이 자연스러운 동작
- 손가락 그립까지 캡처 가능 (배트 잡는 손가락 위치 등)

**리얼리즘 극대화** (실제 MLB 선수 동작 라이선스):
- **KinaTrax 데이터** 또는 **Reboot Motion 데이터** 구매
- MLB 구장 in-game 데이터 활용 가능
- 단, 라이선스 비용이 매우 높음

### 2-3. Move AI 실전 워크플로우

야구 투구 모션을 잡는 가장 빠른 방법:

```
1. iPhone 거치 (선수 측면, 약 5m 거리, 무릎 높이)
2. Move One 앱 실행 → 녹화 시작
3. 선수 투구 (3-5회 반복)
4. 녹화 종료 → 자동 클라우드 업로드
5. 1-2분 내 처리 완료
6. FBX 다운로드 (Mixamo / Unreal Mannequin / 커스텀 스켈레톤)
7. Blender로 임포트 → Auto-Rig Pro Remap으로 캐릭터 리그에 적용
8. UE 5.7로 임포트
```

**팁**: 
- 카메라 위치를 **3가지 각도**(측면, 정면, 위)로 동일 동작을 촬영해두면 후에 Multi-Cam으로 재처리 가능
- 야구장 같은 야외에서는 **밝은 조명 + 고대비 배경**이 정확도를 크게 높임
- 단일 카메라는 occlusion(가려짐)에 약하므로 글러브가 몸을 가리는 동작은 Multi-Cam 필수

### 2-4. 모션 데이터 후처리 워크플로우

AI 모션 캡처는 항상 **약간의 클린업**이 필요합니다. 발 미끄러짐(foot sliding), 떨림(jitter), 자세 비대칭이 흔합니다.

권장 후처리 도구:
1. **Cascadeur** - 클린업 전문, AutoPosing으로 단 몇 클릭에 자세 보정
2. **Blender + Auto-Rig Pro Remap** - 리타게팅 + 발 락(foot lock)
3. **Rokoko Studio** - 그들의 foot locking 필터 사용 (무료)

---

## 3. AI 키프레임 도구 — Cascadeur

### 3-1. Cascadeur가 게임 체인저인 이유

Cascadeur는 키프레임 애니메이션의 **80% 작업을 자동화**합니다. 야구 게임처럼 정확한 신체 메카닉이 중요한 경우 특히 강력합니다.

**핵심 AI 기능:**

| 기능 | 설명 | 시간 단축 |
|---|---|---|
| **AutoPosing** | 한 관절만 움직이면 전신이 자연스럽게 따라옴 | 수시간 → 수분 |
| **AI Inbetweening** | 키 포즈만 잡으면 사이 프레임 자동 생성 (최대 120 프레임) | 수일 → 수십분 |
| **AutoPhysics** | 키프레임을 물리적으로 정확하게 자동 보정 | 수시간 → 즉시 |
| **Ragdoll** | 충돌/낙하 시뮬레이션 | 수십분 → 즉시 |
| **AI Root Motion Tool** | 루트 모션 자동 생성 | 수십분 → 즉시 |

### 3-2. 2026년 Cascadeur 최신 기능 (2025.3 / 2026.1 기준)

**Cascadeur 2025.3 (2025년 11월) 주요 업데이트:**
- AI Inbetweening이 **별도 도구가 아닌 인터폴레이션 시스템에 통합**되어 트랙별 적용 가능
- **Quadruped (4족 동물) AutoPosing** Alpha 지원 (말, 개 등)
- **Quick Rigging Tool** 4족 동물 지원
- **Filament Renderer** 실험적 지원 (PBR 렌더링)

**Cascadeur 2026.1 예정 / Epic MegaGrant 수상:**
- Epic Games로부터 MegaGrant 수상 → **Unreal Engine Live Link 정식 통합** 개발 중
- 실시간 양방향 통신: Cascadeur에서 작업하면 UE에 즉시 반영

### 3-3. 야구 애니메이터를 위한 Cascadeur 워크플로우

**투구 애니메이션 작성 예시** (전통 방식 vs Cascadeur):

전통 키프레임 (Blender):
- 8시간 (와인드업 → 코킹 → 가속 → 릴리즈 → 팔로우스루)
- 각 포즈마다 척추, 골반, 어깨, 팔꿈치 모두 수동 조정

Cascadeur 방식:
- 30분: 5개 핵심 포즈만 잡음 (AutoPosing이 전신 정렬)
- 1분: AI Inbetweening 적용 → 자동으로 사이 프레임 생성
- 10분: AutoPhysics로 물리적 정확도 보정 (관성, 무게 중심)
- **총 40분, 품질은 비슷하거나 더 높음**

### 3-4. Cascadeur ↔ Blender ↔ UE 파이프라인

```
Blender에서 캐릭터 모델링 + 리깅 (또는 Auto-Rig Pro)
        ↓
FBX 익스포트 → Cascadeur 임포트
        ↓
Cascadeur Quick Rigging Tool (Mixamo, UE Mannequin, MetaHuman 자동 인식)
        ↓
키프레임 작업 (AutoPosing + AI Inbetweening)
        ↓
FBX/USD/DAE 익스포트
        ↓
UE 5.7 임포트 → Animation Sequence
```

**가격 정보** (2026.04 기준):
- Free: 비상업적 사용, .casc 포맷만
- Indie: $8/월 (연간), 매출 $100K 이하
- Pro: $33/월 (연간), 무제한 상업 사용, retargeting 포함
- Teams: 사용자당, Discord 우선 지원

야구매니즈 같은 인디 스튜디오는 **Pro** 플랜이 필수입니다.

---

## 4. Blender 워크플로우 가속화

### 4-1. Auto-Rig Pro AI (필수 플러그인)

Blender에서 캐릭터 리깅을 하는 표준 플러그인이며, **최신 버전은 AI 기반 페이셜 마커 자동 배치**를 지원합니다.

**v3.77.38 (Blender 5.1, 2026.04 기준) 신기능:**
- AI 페이셜 예측 "Samples" 설정으로 정확도 향상
- Smart IK Pole - 다리 회전 시 IK 폴 위치 유지 (다리 뒤집힘 방지)
- Quad/Universal/Humanoid 리그 타입
- UE Mannequin / MetaHuman / Mixamo 원클릭 익스포트
- Twist Bone 다중 지원 (게임 엔진에서 볼륨 보존)

**가격**: $50 (전체 패키지)

**핵심 워크플로우**:
1. 캐릭터 메시 임포트
2. Smart 모드 켜고 그린 마커를 손목/팔꿈치/무릎 등에 배치
3. AI가 본 위치 자동 예측
4. Quick Rig 클릭 → 컨트롤 리그 + IK + FK + 페이셜 자동 생성
5. Bind Mesh로 스키닝 (자동 웨이트)
6. 게임 엔진 익스포트 (Unreal/Unity/Godot 프리셋)

### 4-2. Blender MCP — Claude AI로 Blender 자동 조작

**Blender MCP** (ahujasid/blender-mcp)는 Claude AI가 자연어로 Blender를 직접 조작할 수 있게 해주는 오픈소스 통합입니다.

```bash
# 설치
pip install blender-mcp
# Blender Add-on 설치 (addon.py)
# Claude Desktop 설정에 MCP 서버 등록
```

**활용 예시 (자연어로 Claude에게 지시):**

```
야구 글러브 모델을 Hyper3D Rodin으로 생성하고,
Poly Haven에서 가죽 텍스처를 가져와서 적용해줘.
```

```
선택된 캐릭터의 모든 본 이름을 UE Mannequin 컨벤션으로 바꿔줘
(spine_01, clavicle_l 등).
```

```
이 투구 애니메이션의 키프레임을 30프레임마다 분석해서
부자연스러운 자세가 있으면 알려줘.
```

```
씬에 있는 모든 캐릭터의 유니폼 머티리얼을
홈팀 색상 (RGB 220, 0, 50)으로 일괄 변경해줘.
```

**제한사항**: 
- 복잡한 예술적 결정은 여전히 사람의 몫
- 라이팅의 "느낌"이나 컴포지션의 균형은 AI가 판단 못함
- Blender 라이선스: 자유 사용 가능하지만 telemetry는 수동으로 끄기

### 4-3. 다른 유용한 Blender AI 플러그인

| 플러그인 | 용도 | 비용 |
|---|---|---|
| **Animate Anything** | AI 자동 리깅 (15가지 생물 유형) | 무료 |
| **Mantis Rigging Nodes** | 노드 기반 리깅 시스템 | 무료/유료 |
| **CloudRig** | 모듈형 리그 빌더 | 무료 |
| **BlenQuick Auto-Rigger Ultimate** | 자동 마커 배치 + 리깅 | 유료 |
| **SKAVA Auto Rigger Pro** | 휴머노이드/4족 AI 리깅 | 유료 |
| **Snappy Rigger** | 빠르고 사용하기 쉬운 리거 | 유료 |
| **Mixamo Add-on** | Mixamo 자동 리깅 + IK 컨트롤 | 무료 |

### 4-4. Blender Toolkit Claude Code Skill

만약 Claude Code(개발 환경)를 함께 사용한다면, **Blender Skill**을 추가하면 Python 자동화 스크립트 생성이 매우 쉬워집니다:

```
Blender Python으로 50명의 야구선수 캐릭터에
각각 다른 등번호 텍스처를 일괄 적용하는 스크립트를 작성해줘.
번호는 CSV 파일에서 읽어와.
```

이런 식으로 자연어로 요청하면 Claude가 `bpy` API를 사용한 스크립트를 즉시 생성합니다.

---

## 5. AI 3D 모델 생성 + 자동 리깅

### 5-1. AI 3D 모델 생성 도구 비교 (2026년 기준)

야구 게임에서 필요한 3D 자산: 선수 다양한 변형, 야구 장비, 관중, 경기장 소품 등

| 도구 | 특징 | 토폴로지 | PBR | 자동 리깅 | 가격 |
|---|---|---|---|---|---|
| **Hyper3D Rodin (Gen-2)** | 100억 파라미터, 4K PBR, 최고 품질 | 고폴리, 정리 필요 | ★★★★★ | ❌ | $99/월~ |
| **Tripo AI (v3.0)** | 게임용 깔끔한 토폴로지, 자동 리깅 | ★★★★★ (Quad) | ★★★ | ✅ | $12/월~ |
| **Meshy AI** | 안정적, Blender/Unity/UE 플러그인 | ★★★★ | ★★★★ | ❌ (부분) | $14.50/월~ |
| **Hunyuan 3D (Tencent)** | Pro 6분, Rapid 3분 | ★★★ | ★★★ | ❌ | API 기반 |
| **Neural4D (Direct3D-S2)** | 산업용, Quad 토폴로지, 워터타이트 | ★★★★★ | ★★★★ | ❌ | $6.90/월~ |
| **TRELLIS.2** | 20초~4분 | ★★★ | ★★★ | ❌ | API |
| **Stability AI SF3D** | 0.5초 (앨베도 only) | ★★ | ❌ | ❌ | API |

### 5-2. 야구 게임에 가장 적합한 조합

**선수 캐릭터 (정확한 비율 필요):**
- **MetaHuman** 베이스 + 커스터마이징 → UE 5.7 직접 사용
- 또는 **Reallusion Character Creator** → MetaHuman 호환 셋업

**유니폼/장비 (다양한 변형 필요):**
- **Tripo AI**: 글러브, 모자, 배트, 스파이크 등 깔끔한 토폴로지
- **Meshy AI**: 텍스처 품질 우선이라면

**관중/배경 캐릭터 (대량 생성):**
- **Hyper3D Rodin Gen-2**: 포토리얼 4K 텍스처 (히어로 샷용)
- **Tripo AI**: 군중용 (LOD 낮은 메시)

**경기장 디테일 (덕아웃, 광고판, 좌석 등):**
- **Meshy + Poly Haven** (Blender MCP로 통합)

### 5-3. 실전 파이프라인: AI 생성 → Blender → UE

```
1. Hyper3D Rodin Gen-2에서 "야구 글러브, 갈색 가죽, 사용감 있는" 프롬프트
   → 4K PBR 텍스처 OBJ/GLB 다운로드 (~2분)
        ↓
2. Blender 임포트 → 메시 클린업 (Decimate, Remesh)
        ↓
3. Tripo AI에서 자동 리깅 (캐릭터인 경우)
   또는 Auto-Rig Pro로 수동 리깅 (소품인 경우)
        ↓
4. Blender MCP로 UV 정리, LOD 생성 자동화
        ↓
5. FBX/USD 익스포트
        ↓
6. UE 5.7 Static Mesh / Skeletal Mesh로 임포트
        ↓
7. Nanite 활성화 (Static Mesh 자동 LOD)
```

### 5-4. ChatAvatar - 얼굴 사진 → 3D 캐릭터

선수 얼굴을 빠르게 만들고 싶다면:
- **ChatAvatar** (Hyper3D 계열) - 사진 1장 → 리깅된 3D 페이스
- **MetaHuman from Mesh** - UE 5.7에서 메시를 MetaHuman으로 변환
- **AccuRIG** (Reallusion 무료) - 자동 리깅 + ActorCore 모션 라이브러리

---

## 6. Unreal Engine 5.7 애니메이션 신기능

### 6-1. UE 5.7 애니메이션 핵심 기능 정리

UE 5.7 (2025년 11월 출시)은 애니메이션 분야에서 큰 업데이트가 있었습니다:

| 기능 | 상태 | 야구 게임에 활용 |
|---|---|---|
| **Game Animation Sample Project (GASP)** | 정식 (UE 5.4부터, 5.7 업데이트) | 즉시 사용 가능한 500+ 애니메이션 |
| **Mover Plugin** | Experimental | Character Movement 후속, 롤백 네트워킹 |
| **Motion Matching** | Production | 핵심 기술, 야구 게임 필수 |
| **ML Deformer** | Production | 근육/옷 디포메이션 ML 학습 |
| **Pose Search Column in Choosers** | Experimental | Motion Matching과 Chooser 연계 |
| **Smart Object** | Production | NPC가 벤치 앉기 등 환경 상호작용 |
| **Footplacement Control Rig 노드** | 신규 | UAF의 첫 단계 |
| **Unreal Animation Framework (UAF)** | 5.8 예정 | Anim Blueprint 후속 |
| **Mover + Slide 메카닉** | 신규 | 야구 슬라이딩에 직접 활용 |
| **Bone Masking + Animation Mixing** | 신규 | 상체/하체 분리 애니메이션 |
| **Narrative Branching with Cinematic Dialogues** | 신규 | 시나리오 모드 |

### 6-2. Game Animation Sample Project (GASP) — 무료 골드 마인

**GASP는 야구매니저 같은 프로젝트에 가장 가치 있는 무료 자산입니다.**

UE 5.7 업데이트 내용:
- **새 캐릭터 + Mover 플러그인 통합**
- **400개 추가 애니메이션** (총 500개 이상)
- **새 locomotion 데이터셋**
- Smart Object 레벨 (NPC 벤치 착석)
- **Slide 메카닉** (지형 경사 따라 가속/감속) ← **야구 슬라이딩에 직접 사용 가능**
- Pose Search Column in Choosers (실험적)
- Footplacement Control Rig 노드

**다운로드**: Fab 마켓플레이스 무료

야구매니저는 GASP를 베이스로 시작하여, 필요한 동작만 추가하면 개발 시간이 **수개월 단축**됩니다.

### 6-3. Motion Matching — 야구 게임의 핵심

**Motion Matching**은 모션 라이브러리에서 **현재 게임 상태에 가장 적합한 포즈를 매 프레임 검색**하여 재생하는 기술입니다.

**야구 게임에 적용:**
- **수비수**: 공이 어디로 날아가는지에 따라 가장 자연스러운 반응 동작 자동 선택
- **주자**: 베이스 사이 거리/속도에 따라 적절한 주루 모션 선택
- **타자**: 투수의 구종/코스에 따라 다른 스윙 모션 선택
- **투수**: 와인드업 위치/그립에 따라 다양한 투구 폼 매칭

기존의 Blend Space + State Machine보다 **훨씬 자연스럽고 반응성이 좋음**.

**필요한 작업:**
1. 모션 데이터베이스 구축 (수백~수천 개 애니메이션)
2. Pose Search Database 설정
3. Trajectory Generator (입력 → 미래 경로 예측)
4. Motion Matching 노드를 Anim Graph에 추가

UE 5.7 GASP는 **Motion Matching 베스트 프랙티스 셋업**을 무료로 제공합니다.

### 6-4. ML Deformer — 근육과 옷의 자연스러운 변형

**ML Deformer**는 머신러닝으로 학습된 메시 변형 모델입니다.

**작동 방식:**
1. Maya/Houdini 같은 외부 도구에서 고품질 변형 시뮬레이션 데이터 생성 (예: 근육 시뮬레이션, 천 시뮬레이션)
2. UE의 ML Deformer Editor에서 학습 (Python + ONNX 런타임)
3. 게임 런타임에서 **Skeletal Mesh가 ML 모델로 변형**됨

**야구 게임 활용:**
- 투수 어깨 근육이 와인드업에서 자연스럽게 부풀고 수축
- 슬라이딩 시 유니폼이 신체와 자연스럽게 상호작용
- MetaHuman의 사실적인 얼굴 변형

**UE 5.7 ML Deformer 샘플 프로젝트**가 무료로 제공됩니다.

### 6-5. Mover Plugin — Character Movement 후계자

UE 5.7에서 **Experimental → 곧 Production**:
- **롤백 네트워킹** (Network Prediction Plugin 또는 Chaos Networked Physics)
- **블루프린트 친화적**
- 야구 게임의 멀티플레이어 모드에서 강력
- Slide 메카닉이 슬라이딩에 그대로 활용 가능

**현재 상태 (UE 5.7)**: Experimental, Root Motion 작업 중. UE 5.8에서 정식 권장 예정.

### 6-6. Mutable Plugin — 캐릭터 변형 양산

**Mutable**은 런타임에 캐릭터 메시/텍스처/머티리얼을 합성하는 시스템입니다.

**야구 게임 활용:**
- 1000명의 선수를 베이스 메시 1-2개 + 변형 파라미터로 표현
- 신장/체격/얼굴/유니폼/장비를 동적으로 조합
- 메모리 절약 + 다양성 양립

UE 5.6부터 정식 통합되어 5.7에서 안정성 향상.

### 6-7. Niagara × PCG 통합 (UE 5.6+)

야구 게임의 관중 시뮬레이션:
- **PCG**로 좌석 배치 + 관중 분포
- **Niagara**로 관중 애니메이션 (박수, 응원, 반응)
- 두 시스템이 서로의 데이터를 활용 가능

---

## 7. 페이셜 애니메이션과 립싱크

### 7-1. MetaHuman Animator (UE 5.6 정식 통합)

**MetaHuman Animator**는 야구 게임의 캐릭터 표정 작업의 표준입니다.

**3가지 캡처 방식** (모두 지원):

1. **iPhone Live Link Face (ARKit)**
   - 무료, 실시간 스트리밍
   - 52개 ARKit blend shape coefficient → 72-bone facial rig
   - 인터뷰 영상, 컷씬에 즉시 활용

2. **DSLR/웹캠 비디오 업로드**
   - MetaHuman Animator가 후처리로 정밀 분석
   - 영화 수준 페이셜 캡처 가능

3. **오디오 기반 페이셜 애니메이션** (UE 5.5+ 신기능)
   - 오디오 파일만으로 페이셜 애니메이션 생성
   - 다국어 지원 (한국어 포함)
   - 한국어 더빙 → 자동으로 입 모양 일치
   - **야구 중계 멘트, 선수 인터뷰에 매우 강력**

### 7-2. MetaHuman 5.7 (2026년 신기능)

- **Linux/macOS 지원**: MetaHuman Creator가 Linux와 macOS에서도 사용 가능
- **Live Link Face on Android**: iPhone뿐 아니라 Android 기기에서도 페이셜 캡처
- **iPad Live Link Face + 외부 카메라**: DSLR/액션캠과 연결하여 더 좋은 페이셜 캡처
- **Maya 2023~2026 호환** MetaHuman 플러그인
- **Joint-based 헤어 워크플로우**: 헤어 스트랜드를 본으로 컨트롤
- **Hair 키프레임 + 리지드바디 시뮬 블렌딩**: 액션 장면에서 머리 위치 아트 디렉션
- **헤어 키 + 피직스 시뮬 블렌딩** (Experimental)

### 7-3. NeuroSync + Convai (실시간 AI 캐릭터)

게임 내 NPC가 AI로 대답하고 실시간으로 입 모양이 맞게 하려면:

```
플레이어 음성 → Convai AI → LLM 응답 생성 → TTS → NeuroSync → 250+ MetaHuman 블렌드 셰이프
```

야구 게임 활용:
- 코치 NPC와 자유 대화 (선수 발탁 상담 등)
- 라이브 중계 멘트 (상황별 자동 생성)
- 가상 인터뷰 모드

### 7-4. NVIDIA Audio2Face

NVIDIA Omniverse의 **Audio2Face**도 강력합니다:
- 오디오 → 페이셜 애니메이션 자동 생성
- ARKit blend shape 형식으로 익스포트
- UE 5.7로 가져와 MetaHuman에 적용 가능

### 7-5. 야구 게임 페이셜 워크플로우 추천

**컷씬/시네마틱**:
1. 배우가 iPhone Live Link Face로 라이브 연기
2. Take Recorder로 캡처
3. MetaHuman Animator로 정밀 후처리
4. Sequencer에 넣고 카메라/조명 작업

**런타임 NPC 표정 (관중, 동료)**:
1. ML Deformer로 학습된 표정 변형
2. 게임 이벤트 트리거 → 적절한 표정 블렌드 (홈런 시 환호 등)

**한국어 더빙 컷씬**:
1. 한국어 음성 녹음 (성우)
2. MetaHuman Animator의 **Audio Driven Animation** 사용
3. 자동으로 입 모양 + 약간의 표정 생성
4. 필요시 수동 조정

---

## 8. 클로스 / 헤어 / 근육 시뮬레이션

### 8-1. UE 5.7 Chaos Cloth — 야구 유니폼 시뮬레이션

야구 유니폼은 펄럭임, 주름이 매우 중요합니다. **Chaos Cloth**가 표준입니다.

**Chaos Cloth 워크플로우:**

```
Marvelous Designer로 유니폼 패턴 → Maya/Blender로 시뮬 메시 (저폴리) 생성
        ↓
스키닝 (캐릭터 리그에 바인드)
        ↓
UE 임포트 → Skeletal Mesh의 일부로 추가
        ↓
Chaos Cloth Editor에서 시뮬 메시 ↔ 렌더 메시 연결
        ↓
Max Distance 페인팅 (어디까지 자유 이동 가능한지)
        ↓
Physics Asset에 콜리전 캡슐 추가
        ↓
Wind, Gravity, Damping 등 파라미터 조정
```

**야구 게임 특화 팁:**
- 투구 시 유니폼 셔츠가 어깨/팔에 따라 움직임
- 슬라이딩 시 흙먼지 + 유니폼 마찰
- 모자가 머리에 고정되도록 적절한 콜리전 설정
- 글러브 끈이 자연스럽게 움직이도록 별도 시뮬 메시 추가

### 8-2. 시네마틱 렌더링에서 클로스 캐싱

**Movie Render Queue + Sub-sampling** 사용 시 클로스가 깨지는 문제 해결:

1. Take Recorder로 클로스 시뮬 캐싱
2. Sequencer에 캐시 적용
3. Sub-sample 64 등으로 안전하게 렌더 가능

(Beatrice Schmidt가 공유한 워크플로우)

### 8-3. ML Deformer로 클로스 학습

매번 클로스 시뮬을 돌리기는 너무 무겁습니다. **ML Deformer**로 미리 학습:

1. Maya/Houdini에서 다양한 동작에서 클로스 시뮬 결과 데이터 생성
2. UE ML Deformer로 학습
3. 런타임에서는 ML 모델이 클로스 변형을 즉시 계산 (시뮬 불필요)

**결과**: 시뮬 없이 시뮬 같은 자연스러움 + 모바일에서도 실행 가능

### 8-4. 헤어 시뮬레이션 (UE 5.7 신기능)

UE 5.7의 **Groom 플러그인 업데이트**:
- **Joint-based 헤어**: 헤어 스트랜드를 본으로 컨트롤
- **키프레임 + 시뮬 블렌딩**: 머리카락이 자연스러우면서도 액션 순간에는 아트 디렉션 가능
- 예: 타자가 스윙할 때 머리카락이 휘날림 + 클로즈업에서 자연스럽게 정리

### 8-5. 근육 시뮬레이션

선수의 근육이 동작에 따라 자연스럽게 부풀고 수축하는 효과:

**옵션 1: Chaos Flesh (UE 5.5+)**
- 음성근(soft body) 시뮬레이션
- 무겁지만 매우 사실적

**옵션 2: ML Deformer (추천)**
- Houdini나 외부 시뮬 결과를 학습
- 런타임 매우 가벼움
- MLB 선수 같은 프로 운동선수의 근육을 사실적으로 표현 가능

---

## 9. 생성형 AI 텍스트→애니메이션

### 9-1. SayMotion (DeepMotion) — 텍스트로 애니메이션 생성

**SayMotion**은 텍스트 프롬프트로 휴머노이드 애니메이션을 생성하는 도구입니다.

```
프롬프트: "야구 선수가 베이스로 헤드퍼스트 슬라이딩"
→ FBX/GLB/BVH 다운로드 (몇 초 내)
```

**SayMotion 2.4 주요 기능:**
- **400,000개 모션 클립** 학습 데이터셋
- **Inpainting**: 기존 애니메이션의 일부만 수정/확장
- **Generative Merge**: 두 애니메이션을 자연스럽게 연결
- **Prompt Craft**: 512단어까지의 "스토리"를 자동으로 일련의 프롬프트로 분해
- **Rerun**: 다른 캐릭터에 즉시 리타겟

**가격**: 
- 무료 25 크레딧/월 (비상업)
- $15/월 (50 크레딧, 상업)
- $300/월 (1000 크레딧)

**야구 게임 활용:**
- 프로토타이핑 단계: 빠르게 컨셉 검증
- "이런 동작이 가능한가" 즉시 시각화
- 프로덕션은 Move AI나 Cascadeur로 정밀하게

### 9-2. Cartwheel — OpenAI/Pixar 출신이 만든 신흥 강자

**Cartwheel**:
- 창업자: Andrew Carr (전 OpenAI, ChatGPT/Codex 개발), Jonathan Jarvis (전 Google Creative Lab)
- 팀: Pixar (Inside Out, Coco), Sony Pictures Animation, Riot Games 출신
- 비공개 베타 60,000명 → 2025년 5월 정식 출시

**3가지 입력 방식:**
1. 스마트폰으로 모션 녹화
2. 텍스트 프롬프트
3. 라이브러리에서 모션 선택

**출력**: Unity, Unreal Engine, Maya, Blender 직접 익스포트

**브라우저 기반**, 무료 티어 있음. 야구 게임에 어떻게 적합한지는 베타 사용 후 판단 필요.

### 9-3. 텍스트→애니메이션의 한계

이 기술이 만능은 아닙니다:
- **물리적 정확도**: AI가 만든 모션은 종종 실제 신체 메카닉을 어김
- **세부 디테일**: 손가락, 발, 머리 위치 등은 부정확할 수 있음
- **스타일 일관성**: 같은 캐릭터의 다른 동작이 일관되지 않을 수 있음

**추천 활용**:
- 프로토타이핑, 컨셉 검증
- 백그라운드 NPC 동작
- "참고용" 모션 (그 위에 키프레임으로 정제)

---

## 10. 야구 게임 특화 워크플로우

### 10-1. 야구 게임 애니메이션의 분류

야구 게임에서 필요한 애니메이션을 정리:

**투수 (Pitcher)**:
- 와인드업 (5-10가지 스타일: 정통파, 사이드암, 언더스로 등)
- 셋포지션
- 투구 동작 × 구종 (포심, 슬라이더, 커브, 체인지업, 너클볼 등 = 약 50가지)
- 견제구 (1루, 2루, 3루)
- 견제 후 투구
- 마운드 정리, 사인 교환, 공 받기
- 부상 모션, 흥분 모션

**타자 (Batter)**:
- 타석 진입, 자세 잡기 (5-10가지 스탠스)
- 스윙 (풀스윙, 짧은 스윙, 번트 = 약 20가지)
- 헛스윙, 파울, 컨택트 변형
- 타구 후 1루 출발
- 백스윙, 폼업

**주자 (Runner)**:
- 리드 (1차, 2차)
- 베이스 도루
- 헤드퍼스트/피트퍼스트 슬라이딩
- 베이스 회피 (백슬라이드)
- 홈인 모션

**수비수 (Fielder)**:
- 다이빙 캐치 (전방, 좌/우)
- 점프 캐치
- 펜스 점프
- 송구 (오버핸드, 사이드, 언더, 점프 송구)
- 더블플레이 핸들링
- 베이스 커버

**기타**:
- 더그아웃 셀러브레이션
- 홈런 셀러브레이션 (배트 플립 포함)
- 마운드 회의
- 심판 동작 (스트라이크, 볼, 아웃, 세이프)

**총 합계: 최소 300~500개 동작, 변형 포함시 1000+**

### 10-2. 효율적인 모션 캡처 계획

**전통적 방식**: 스튜디오 1주일 × 5명 (약 1억원)

**AI 활용 방식**:

```
1단계: Move Multi-Cam (iPhone 4-6대) + 실제 야구선수 1-2명 섭외
  → 이틀 만에 핵심 동작 200개 수집 (예산 500만원)

2단계: Cascadeur로 변형 생성
  → 캡처한 1개 투구 → AI Inbetweening + AutoPosing으로 5가지 변형 생성
  → 200개 → 1000개로 확장

3단계: SayMotion으로 보조 동작
  → "심판이 스트라이크 외친다", "관중이 기립박수" 등 자잘한 동작
  → 즉시 생성

4단계: Blender + Auto-Rig Pro Remap
  → Move 데이터를 모든 선수 캐릭터에 일괄 리타겟

5단계: UE 5.7 Motion Matching Database 구축
  → 자동으로 적합한 모션 선택
```

**예상 절감**: 8000만원 + 6주 시간 절감

### 10-3. 투구 모션 라이브러리 구축 사례

투구 1개 동작을 풍부하게 만드는 방법:

**기준 동작 (실제 선수 캡처):**
- 포심 패스트볼 - 정통파 - 우투

**Cascadeur로 파생:**
- 좌투 버전 (Mirror Tool, 1초)
- 사이드암 버전 (AutoPosing으로 팔 각도 조정, 5분)
- 언더스로 버전 (5분)
- 부상 후 부자연스러운 버전 (AutoPhysics 끔, 5분)
- 피로한 버전 (속도 조정 + 미세 변형, 5분)
- 와일드 피치 (릴리즈 포인트 변경, 5분)
- 견제 후 즉시 투구 (앞 모션과 연결, 10분)

**구종 변형:**
- 슬라이더: 손목 비틂 강화 (Custom Layer)
- 커브: 팔 스윙 궤도 변경
- 체인지업: 그립만 변경 (모션 동일)

이렇게 1개 베이스 모션에서 **20-30개 변형**을 1시간 내에 생성 가능.

### 10-4. 클로스/디테일 전략

**유니폼:**
- 베이스 메시 + Chaos Cloth 시뮬 (히어로 샷용)
- ML Deformer로 학습 (게임 플레이용, 가벼움)
- 더러워짐 표현: Decal + Vertex Color로 실시간 흙먼지

**모자/헬멧:**
- 모자: Physics Constraint로 머리에 살짝 흔들림
- 헬멧: Static
- 슬라이딩 시 모자 떨어짐: Physics Asset + 트리거

**글러브:**
- 글러브 끈/웹: Chaos Cloth (간단한 시뮬)
- 손가락 그립: Hand IK + Move Multi-Cam 캡처

**스파이크 자국:**
- Decal Stamping + Niagara 흙먼지 파티클
- Footstep 사운드 + 스파이크 자국 자동 생성

### 10-5. 관중 시스템

**전통 방식**: 수만 개 캐릭터 = 메모리 폭발

**최신 AI/UE 방식**:

```
1. Mutable Plugin으로 베이스 캐릭터 + 변형 (체격/유니폼/모자)
2. PCG로 좌석 자동 배치
3. Niagara로 관중 애니메이션 (박수, 함성)
4. Motion Matching으로 그룹 단위 반응 (홈런 시 일제히 일어섬)
5. 멀리 있는 관중은 빌보드 + 단순 애니메이션
```

---

## 11. Blender ↔ UE 5.7 파이프라인 최적화

### 11-1. Send to Unreal 플러그인

Epic 공식 Blender → UE 익스포트 플러그인입니다:
- 자동으로 FBX 익스포트 + UE에 임포트
- 본/스키닝/머티리얼 매핑 자동
- 변경 시 즉시 동기화

### 11-2. USD 파이프라인 (권장)

**FBX보다 USD 사용을 권장:**
- Pixar 표준
- Blender, UE 5.7 모두 정식 지원
- 메타데이터 보존 우수
- 비파괴적

UE 5.7 USD Stage Editor로 Blender USD 파일을 라이브 편집 가능.

### 11-3. 본 컨벤션 통일

**중요**: 모든 도구가 같은 본 이름을 쓰도록 통일하세요.

**추천: UE Mannequin 컨벤션**:
- `pelvis`, `spine_01`, `spine_02`, ...
- `clavicle_l`, `upperarm_l`, `lowerarm_l`, `hand_l`
- `thigh_l`, `calf_l`, `foot_l`, `ball_l`

**또는: MetaHuman 컨벤션** (얼굴 본까지 호환):
- 72-bone facial rig
- Body는 UE Mannequin과 동일

Cascadeur, Auto-Rig Pro, Move AI 모두 UE Mannequin / MetaHuman을 자동 인식합니다.

### 11-4. 리타게팅 워크플로우

```
Move AI 캡처 (자체 스켈레톤)
        ↓
Blender Auto-Rig Pro Remap → UE Mannequin 본 이름으로 변환
        ↓
FBX 익스포트
        ↓
UE 5.7 IK Retargeter → MetaHuman / 커스텀 캐릭터에 적용
        ↓
Motion Matching Database에 추가
```

### 11-5. 자동화 스크립트 권장 목록

Blender Python 또는 UE Python으로 자동화하면 좋은 작업들:

| 작업 | 도구 | 시간 절감 |
|---|---|---|
| 새 캐릭터 일괄 임포트 | UE Python Editor Script | 시간당 50개 |
| 본 이름 일괄 변경 | Blender Python | 즉시 |
| 애니메이션 일괄 리타겟 | UE Python | 시간당 100개 |
| LOD 자동 생성 | Blender Decimate + Bake | 캐릭터당 1분 |
| 머티리얼 일괄 적용 | UE Python | 즉시 |
| Naming Convention 검증 | Blender Python | 즉시 |

이런 스크립트는 **Claude Code**에 자연어로 요청하면 즉시 생성 가능합니다.

---

## 12. 추천 도입 로드맵 (3개월)

### Month 1: 기반 도구 도입

**Week 1-2: 학습 + 기본 셋업**
- Move One 다운로드, 셀프 모션 캡처 연습
- Cascadeur Free 버전으로 기본 워크플로우 학습
- Blender Auto-Rig Pro 구입 + 학습
- UE 5.7 GASP 다운로드, 구조 파악

**Week 3-4: 첫 실전 적용**
- Move One으로 야구 핵심 동작 10개 캡처 (투구, 스윙, 슬라이딩 등)
- Cascadeur로 클린업 + 변형
- UE 5.7에 임포트, GASP 위에 통합

### Month 2: 프로덕션 파이프라인 구축

**Week 5-6: AI 캐릭터 생성**
- MetaHuman으로 베이스 선수 캐릭터 5명 제작
- Mutable Plugin으로 변형 시스템 구축
- Tripo AI로 야구 장비 (글러브, 모자, 배트) 생성

**Week 7-8: 페이셜 + 클로스**
- MetaHuman Animator 워크플로우 셋업
- Audio Driven Animation으로 한국어 멘트 테스트
- Chaos Cloth로 유니폼 시뮬 셋업

### Month 3: 양산 + 최적화

**Week 9-10: 모션 라이브러리 구축**
- Move Multi-Cam으로 실제 야구선수 캡처 (1-2일)
- Cascadeur로 변형 양산 (200개 → 1000개)
- UE Motion Matching Database 구축

**Week 11-12: 최적화 + 자동화**
- ML Deformer 학습 (근육 + 클로스)
- Blender MCP로 자동화 스크립트 작성
- 프로파일링 + 모바일 최적화

---

## 13. 비용 비교 및 ROI

### 13-1. 도구별 월 비용 (인디 스튜디오 기준)

| 도구 | 월 비용 | 필수도 |
|---|---|---|
| Move One | $30 | 필수 |
| Move Multi-Cam | $30 (연 $365) | 권장 |
| Cascadeur Pro | $33 | 필수 |
| Auto-Rig Pro | $50 (1회) | 필수 |
| Blender | 무료 | - |
| MetaHuman | UE 라이선스 포함 | - |
| Tripo AI | $12 | 권장 |
| Hyper3D Rodin | $99 | 선택 |
| SayMotion | $15 | 선택 |
| Cartwheel | 베타 | 선택 |
| Reallusion CC + iClone | $499 (1회) | 선택 |

**총 월 비용 (필수만)**: 약 $63 + 일회성 $50 = **약 9만원/월**

**전통 방식 비교**:
- 모션 캡처 스튜디오 1일 임대: 200-500만원
- 외주 애니메이터 1명 월급: 400-700만원
- 모션 캡처 슈트 (Rokoko Smartsuit): 200만원

### 13-2. ROI 추정

야구 게임 1년 개발 기준:

**전통 방식**:
- 애니메이터 3명 × 12개월 × 500만원 = **1억 8천만원**
- 모션 캡처 외주 = **5천만원**
- 총: **2억 3천만원**

**AI 활용 방식**:
- 애니메이터 1명 × 12개월 × 500만원 = **6천만원**
- AI 도구 비용 = **120만원/년**
- 모션 캡처 셀프 (Move Multi-Cam) = **500만원**
- 총: **6,620만원**

**절감액: 1억 6천만원 (약 70% 절감)**

이는 비용만이 아니라, **반복 작업의 정신적 부담** 감소도 큽니다. 애니메이터가 창의적 결정에 집중할 수 있게 됩니다.

### 13-3. 품질 측면

품질도 떨어지지 않습니다. 오히려:

- Move AI: AAA 스튜디오와 동급 품질 (단일 카메라 기준)
- Cascadeur: 물리적 정확도 측면에서 수동 키프레임보다 우월
- ML Deformer: Pixar/ILM 수준의 디포메이션을 게임 런타임에서
- MetaHuman Animator: 영화 페이셜 캡처 수준

---

## 14. 레퍼런스

### 모션 캡처
- Move AI: [https://move.ai](https://move.ai)
- DeepMotion: [https://www.deepmotion.com](https://www.deepmotion.com)
- Rokoko Vision: [https://vision.rokoko.com](https://vision.rokoko.com)
- KinaTrax (야구 특화): [https://www.kinatrax.com](https://www.kinatrax.com)
- Uplift (야구 특화): [https://www.uplift.ai/baseball](https://www.uplift.ai/baseball)
- Reboot Motion (야구 특화): [https://rebootmotion.com/baseball](https://rebootmotion.com/baseball)

### AI 키프레임
- Cascadeur: [https://cascadeur.com](https://cascadeur.com)
- Cascadeur 2025.3 릴리즈 노트: [https://cascadeur.com/blog/view/cascadeur-2025-3-new-inbetweening-quadrupeds](https://cascadeur.com/blog/view/cascadeur-2025-3-new-inbetweening-quadrupeds)

### Blender 도구
- Auto-Rig Pro: [https://superhivemarket.com/products/auto-rig-pro](https://superhivemarket.com/products/auto-rig-pro)
- Blender MCP: [https://github.com/ahujasid/blender-mcp](https://github.com/ahujasid/blender-mcp)
- Mixamo Blender Add-on: [https://www.adobe.com/products/substance3d/plugins/mixamo-in-blender.html](https://www.adobe.com/products/substance3d/plugins/mixamo-in-blender.html)

### AI 3D 모델 생성
- Tripo AI: [https://www.tripo3d.ai](https://www.tripo3d.ai)
- Meshy AI: [https://www.meshy.ai](https://www.meshy.ai)
- Hyper3D Rodin: [https://hyper3d.ai](https://hyper3d.ai)
- Neural4D: [https://blog.neural4d.com](https://blog.neural4d.com)

### Unreal Engine 5.7
- Game Animation Sample Project: [https://www.unrealengine.com/tech-blog/explore-the-updates-to-the-game-animation-sample-project-in-ue-5-7](https://www.unrealengine.com/tech-blog/explore-the-updates-to-the-game-animation-sample-project-in-ue-5-7)
- Motion Matching: [https://dev.epicgames.com/documentation/en-us/unreal-engine/motion-matching-in-unreal-engine](https://dev.epicgames.com/documentation/en-us/unreal-engine/motion-matching-in-unreal-engine)
- ML Deformer: [https://dev.epicgames.com/documentation/en-us/unreal-engine/ml-deformer-framework-in-unreal-engine](https://dev.epicgames.com/documentation/en-us/unreal-engine/ml-deformer-framework-in-unreal-engine)
- Mover Plugin: [https://dev.epicgames.com/documentation/en-us/unreal-engine/mover-features-and-concepts-in-unreal-engine](https://dev.epicgames.com/documentation/en-us/unreal-engine/mover-features-and-concepts-in-unreal-engine)

### MetaHuman
- MetaHuman 5.7 릴리즈: [https://www.metahuman.com/en-US/releases/metahuman-5-7-is-now-available](https://www.metahuman.com/en-US/releases/metahuman-5-7-is-now-available)
- Audio Driven Animation: [https://dev.epicgames.com/documentation/en-us/metahuman/audio-driven-animation](https://dev.epicgames.com/documentation/en-us/metahuman/audio-driven-animation)
- Convai (실시간 AI NPC): [https://convai.com](https://convai.com)

### 생성형 애니메이션
- SayMotion: [https://www.deepmotion.com/saymotion](https://www.deepmotion.com/saymotion)
- Cartwheel: [https://getcartwheel.com](https://getcartwheel.com)

### Reallusion (대안 워크플로우)
- Character Creator + iClone: [https://www.reallusion.com/metahuman/](https://www.reallusion.com/metahuman/)

### 사내 자료
- 기획팀 매뉴얼: `vscode.md`
- Unity 가이드: `unity-claude-code-guide.md`
- AWS 서버 가이드: `aws-server-claude-code-guide.md`
- Unreal 개발자 가이드: `unreal-claude-code-guide.md`
- Unreal 그래픽 가이드: `unreal-graphics-claude-code-guide.md`

---

## 부록 A: 빠른 시작 — 1주일 만에 100개 동작 양산하기

목표: **혼자서 1주일 만에 야구 게임용 핵심 모션 100개 만들기**

### Day 1: 셋업
- Move One 구매, 본인 모션 5개 캡처 (테스트)
- Cascadeur Pro 구매, 튜토리얼 1시간
- UE 5.7 GASP 다운로드, 기존 모션 확인

### Day 2: 핵심 캡처
- 야구공/배트/글러브 준비
- iPhone 거치 (3가지 각도 동시 촬영)
- 본인 직접 시연: 투구 10가지, 스윙 10가지, 수비 10가지, 주루 5가지 = 35개
- Move AI로 일괄 처리 (1-2시간)

### Day 3: Cascadeur 변형
- 35개 베이스 → 각각 3-5가지 변형 생성
- 미러링, 속도 조정, 강도 조정
- 결과: 100+ 모션

### Day 4: 클린업
- 발 미끄러짐 수정 (Cascadeur Fulcrum Motion Cleaning)
- 어색한 자세 보정 (AutoPosing)
- 시작/끝 자연스럽게 (Inbetweening)

### Day 5: UE 임포트
- IK Retargeter로 UE Mannequin → MetaHuman
- Motion Matching Database 구축
- Pose Search Database 설정

### Day 6: 통합 테스트
- 게임에 적용
- 트랜지션 부자연스러운 부분 보완
- 추가 모션 캡처 (필요시)

### Day 7: 최적화
- ML Deformer 학습 (선택)
- 모바일 LOD 검토
- 문서화

---

## 부록 B: 의사결정 체크리스트

**"이 동작은 어떻게 만들지?"** 빠른 결정을 위한 체크리스트:

```
Q1: 동작이 정확한 신체 메카닉을 요구하는가? (투구, 스윙 등)
   YES → Move AI (모션 캡처) + Cascadeur (보정)
   NO → SayMotion (생성형) 또는 GASP (기존 라이브러리)

Q2: 동작 길이가 5초 이상인가?
   YES → 모션 캡처 (Move Multi-Cam 권장)
   NO → 키프레임 (Cascadeur)

Q3: 페이셜 표현이 필요한가?
   YES → MetaHuman Animator (배우 + iPhone)
   AUDIO ONLY → Audio Driven Animation

Q4: 같은 동작의 변형이 많이 필요한가?
   YES → Cascadeur AI Inbetweening + 변형
   NO → 단일 캡처

Q5: 게임 런타임에서 동적으로 생성되어야 하는가?
   YES → Motion Matching + ML Deformer
   NO → 미리 만든 클립

Q6: 옷/머리/근육 변형이 중요한가?
   히어로 샷 → Chaos Cloth/Groom/Flesh 시뮬
   게임 플레이 → ML Deformer로 학습
```

---

> 📝 이 가이드에 대한 질문이나 개선 사항은 CEO 미니에게 전달해주세요.  
> 새로 발견한 도구나 더 나은 워크플로우가 있으면 팀에 공유 부탁드립니다.  
> AI 애니메이션 분야는 매우 빠르게 변화하므로, 분기마다 이 문서를 업데이트할 예정입니다.
