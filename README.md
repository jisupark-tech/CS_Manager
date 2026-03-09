# CS Manager AI — Customer Support Operations

> 게임 CS(고객지원) 업무를 AI로 자동화하는 프로젝트.
> AI Company 12개 역할 중 **CS Manager** 페르소나 구축 + CS Bot 구현을 담당합니다.

---

## Overview

| 항목 | 내용 |
|------|------|
| 역할 | CS Manager (고객지원) |
| 핵심 업무 | 불만 패턴 분석, FAQ 관리, 에스컬레이션, VOC 분석 |
| 연계 역할 | QA Manager (버그 리포트), PM (제품 피드백), CTO/AI Workflow (수정 요청) |
| 스케일 | 인스턴스 ×1~5 (문의량에 따라 동적 확장) |

## Project Structure

```
CS_Manager/
├── README.md
└── CS_AI/
    ├── 10_cs.md                          # CS Manager 인터뷰 요청서 (Q1~Q40, 16문항 역할특화)
    ├── CS_운영_AI_대체_기획안.md             # CS/운영 AI 대체 3가지 접근법 비교
    ├── GameScale_서비스_분석.md             # GameScale(넥슨) 서비스 분석 레퍼런스
    └── implementation/
        ├── Phase_0_프로젝트_기반.md         # 공통 인프라 세팅 (Week 0~1)
        ├── Phase_1_CS_Bot.md              # CS Bot 구현 (Week 1~3)
        └── templates/
            ├── env_template.env           # 환경변수 템플릿
            ├── faq_template.yaml          # FAQ 데이터 입력 양식
            ├── escalation_rules.yaml      # 에스컬레이션 규칙 정의
            └── game_config.yaml           # 게임별 기본 설정
```

## Interview Questionnaire (인터뷰 요청서)

**파일**: [`CS_AI/10_cs.md`](CS_AI/10_cs.md)

CS Manager 페르소나 구축을 위한 작성 요청서입니다. 총 40문항:

| 섹션 | 내용 | 문항 |
|------|------|------|
| A~E | 공통 질문 (역할 정체성, 의사결정, 워크플로우, 암묵지, 핸드오프) | Q1~Q17 |
| F | AI 멀티 인스턴스 운영 | Q18~Q22 |
| G | 마무리 | Q23~Q24 |
| **H** | **티켓 분류 체계와 SLA** | **Q25~Q27** |
| **I** | **표준 답변과 매크로** | **Q28~Q29** |
| **J** | **자체 해결과 에스컬레이션** | **Q30~Q31** |
| **K** | **클레임 대응과 보상 정책** | **Q32~Q33** |
| **L** | **VOC 분석과 제품 연결** | **Q34~Q36** |
| **M** | **CS 운영 도구와 데이터** | **Q37~Q38** |
| **N** | **주기적 업무와 리포팅** | **Q39~Q40** |

### 핵심 포인트
- **Q30**: CS→QA 버그 에스컬레이션 흐름 (QA Manager Q30과 양방향 연결)
- **Q34~Q36**: VOC 데이터에서 제품 개선안 도출 프로세스
- **Q25**: 티켓 유형별 SLA 매트릭스 (응답/해결 시간 기준)

## CS Bot Implementation (구현)

| Phase | 내용 | 기간 |
|-------|------|------|
| Phase 0 | 프로젝트 기반 (공통 인프라) | Week 0~1 |
| Phase 1 | CS Bot (FAQ/계정/결제 자동응답, 에스컬레이션) | Week 1~3 |

### Tech Stack

| Component | Technology |
|-----------|-----------|
| LLM | Claude API (Sonnet 4.6) |
| Vector DB | ChromaDB (FAQ/문서 검색) |
| Backend | Python 3.11+ / FastAPI |
| Channel | Discord.py / KakaoTalk API |

## Related Repos

| Repo | 역할 |
|------|------|
| [QA_MANAGER](https://github.com/jisupark-tech/QA_MANAGER) | QA Manager AI — 품질 관리, 버그 트리아지, 테스트 자동화 |
| [AI_Company](https://github.com/jisupark-tech/AI_Company) | AI Company 전체 — 12개 역할 페르소나 집합체 |

### CS ↔ QA 연계

```
유저 문의 → CS 접수 → [CS 1차 분류] → 버그 판단 시 QA 전달
                                         ↓
                              QA 재현 확인 → 개발팀 전달 → 수정
                                         ↓
                              QA 검증 완료 → CS 회신 → 유저 안내
```

---

*CS Manager AI v1.0 — 2026.03*
