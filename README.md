# legal-polish-public — 대한민국 법률문서 윤문가이드 (공개판)

> **법률문서 윤문가이드** — 의미는 보존하고 문장·표현·구성만 다듬는다
>
> 쥬리서포트 주식회사 ([jurisupport.com](https://jurisupport.com))

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Platform](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux%20%7C%20Windows-lightgrey)
![Locale](https://img.shields.io/badge/Locale-ko--KR-red)
![Claude Code](https://img.shields.io/badge/Claude%20Code-Required-orange)

---

**대한민국 법률실무**에서 쓰는 한국어 법률문서(준비서면·답변서·의견서·상소이유서·소장 등)의 초안을 받아, **의미(법리·사실·수치 등)는 보존하고 문장·표현·구성만** 다듬는 Claude Code 스킬입니다. 백지에서 새로 쓰는 것이 아니라, 이미 작성된 초안을 손보는 작업입니다.

대한민국 민사·형사 소송실무의 서면 유형과 국립국어원 공공 어문규범을 기준으로 삼으므로, 한국 법원에 제출하는 서면을 다듬는 데 맞춰져 있습니다.

- **버전**: 1.0.0
- **라이선스**: MIT (스킬 자체). 윤문 대상 문서의 권리는 그 문서 권리자에게 있습니다.
- **대상**: 대한민국 법률문서 (한국어, 한국 소송실무)
- **언어/지역**: ko-KR
- **배포**: 공개 가능 (직접 작성한 오리지널 자료 — 근거는 아래 참조)

## 무엇을 하나

탐지 → 윤문 → 충실도감사 3단계로, 다음만 손댑니다: 문체·리듬·표현·문장구성. 다음은 **보존 대상으로 두고 손대지 않습니다**: 법리·주장·결론, 사실관계·인과·순서, 날짜·금액·수치·당사자명·고유명사, 법령 조문·판례 번호·인용문·증거표시(갑/을 제○호증). 의미가 흔들릴 위험이 있으면 고치지 않고 코멘트로만 제안합니다.

## 설치

이 레포는 **Claude Code 플러그인**이자, 그 안의 스킬 폴더를 그대로 복사해 쓰는 **단독(standalone) 스킬**입니다. 둘 중 편한 방법을 고르세요.

### 방법 1 — 플러그인으로 설치 (권장)

터미널에서 마켓플레이스를 한 번 등록한 뒤 설치합니다.

```bash
claude plugin marketplace add https://github.com/jurisupport/legal-polish-public.git
claude plugin install legal-polish-public@legal-polish-public
```

설치가 끝나면 새 Claude Code 세션부터 자동으로 쓸 수 있습니다. 이미 열린 세션에서는 다음을 실행합니다.

```text
/reload-plugins
```

설치 상태는 `claude plugin list`로 확인합니다.

### 방법 2 — 단독 스킬로 복사

레포의 `skills/legal-polish-public/` 폴더를 Claude Code 스킬 디렉터리에 폴더째 복사합니다.

```
~/.claude/skills/legal-polish-public/             # 사용자 전역
# 또는
<프로젝트>/.claude/skills/legal-polish-public/    # 프로젝트 한정
```

예: `git clone` 후 `cp -R legal-polish-public/skills/legal-polish-public ~/.claude/skills/`

### 사용

설치 후 다음과 같이 말하면 작동합니다: "이 준비서면 윤문해줘", "법률문장 매끄럽게", "서면 군더더기 빼줘".

## 모드

| 모드 | 적용 | 처리 |
|---|---|---|
| **경량(기본)** | 문단·짧은 서면(≈3,000자 이하) | 탐지·윤문·자체검증을 한 패스로 |
| **정밀**(`--정밀`·제출용·장문) | 긴 서면·제출 임박 | 탐지(2회 독립 실행 후 결과 합치기) → 윤문 → 충실도감사를 단계 분리 |

정밀 모드는 탐지를 **2회 독립으로 실행해 두 결과를 하나로 합칩니다**. 한 번의 탐지는 긴 문서에서 회차마다 다른 항목을 놓치므로, 두 번 돌려 결과를 합치면 누락이 크게 줍니다.

## 구성

```
.claude-plugin/
  plugin.json                    플러그인 매니페스트
  marketplace.json               마켓플레이스 메타(/plugin marketplace add 용)
LICENSE                          MIT
README.md                        이 파일
skills/legal-polish-public/      ← 단독 스킬로 쓸 때 이 폴더를 복사
  SKILL.md                       스킬 본문(철칙·모드·워크플로우·출력형식)
  references/
    principles.md                9개 작법 원칙(간결성·문장길이·호응·능동·…)
    grammar-norms.md             어문규범(띄어쓰기·맞춤법·문장부호)
    detection-checklist.md       누락 방지용 전수 점검 절차(패스 0~Z)
    examples.md                  오리지널 ✗→✓ 예문 모음
    doc-types.md                 문서 종류별 점검 포인트
    SOURCES.md                   근거·저작권 고지
```

핵심 설계: **규칙(principles·grammar-norms)** 과 **그 규칙을 빠짐없이 적용하게 만드는 절차(detection-checklist의 전수 점검 패스)** 를 분리했습니다. 규칙만 있고 빠짐없이 훑는 절차가 없으면 실제 출력에서 빠지기 때문입니다.

## 출처·근거

이 스킬의 규칙·예문·서술은 **국립국어원 공공 어문규범과 일반적으로 알려진 한국어 작법 지식에 근거해 직접 작성한 자료**입니다. 공공 어문규범은 자유롭게 이용할 수 있는 공공저작물이고, '문장은 짧게'·'불필요한 피동을 줄여라' 같은 작법 원칙은 누구나 쓸 수 있는 일반 지식입니다. 그래서 이 자료는 자유롭게 공개·배포할 수 있습니다. 상세 근거는 `references/SOURCES.md` 참조.

## 사용자 데이터 주의

윤문 대상으로 넣는 실제 서면·사건정보는 이 스킬의 자산이 아닙니다. 공개 예시로 전환할 때는 당사자·사건정보를 가상으로 치환하세요(의뢰인 비밀 보호).

---

## 만든 곳

**쥬리서포트 주식회사** — 대한민국 송무 변호사용 AI 통합 작업환경
[jurisupport.com](https://jurisupport.com) · admin@jurisupport.com

이 스킬은 쥬리서포트 주식회사가 공개·배포하는 오리지널 자료입니다. 변호사용 통합 패키지는 [jurisupport/jurisupport-plugins](https://github.com/jurisupport/jurisupport-plugins)를 참고하세요.

© 2026 쥬리서포트 주식회사. MIT License.
