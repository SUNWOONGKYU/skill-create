# skill-create-코어5 (V3.14)

Claude Code용 **"스킬을 만드는 스킬"** — 막연한 요청을 9-Phase 제조 공장으로 돌려 단일 책임·자기완결 SKILL.md를 출하한다.

> 자매 공장: **에이전트 만드는 스킬** → [SUNWOONGKYU/llm-dependent-agent-create](https://github.com/SUNWOONGKYU/llm-dependent-agent-create) (별칭 "에신")

## 무엇을 만드나
Claude Code 스킬(SKILL.md)을 9-Phase 방식으로 제조. 발굴 → 분해 → 검증 → 조립 → QC 출하검사 → 운영 루프. 단일 책임·자기완결·500줄 권장 — 거대 스킬을 만들지 않는다.

- 모드: 단일 / 배치
- 산출물: `~/.claude/skills/{name}/SKILL.md`

## ⚡ 가장 빠른 설치 — Claude Code에게 시키기

본인 Claude Code 세션에 아래 한 줄을 붙여넣으세요. 알아서 받아서 `~/.claude/skills/`에 설치합니다.

> **"`SUNWOONGKYU/skill-create` 설치해 줘."**

## 직접 설치

### git clone (권장 — `git pull`로 갱신 쉬움)
```bash
git clone https://github.com/SUNWOONGKYU/skill-create.git
# macOS·Linux
cp -r skill-create/skill-create-코어5 ~/.claude/skills/
# Windows: cp -r skill-create/skill-create-코어5 "$env:USERPROFILE\.claude\skills\"
```

### ZIP (Git 모르는 분)
1. https://github.com/SUNWOONGKYU/skill-create 접속
2. 녹색 `Code` → `Download ZIP`
3. 압축 풀고 `skill-create-코어5` 폴더를 `~/.claude/skills/` 안으로 복사

### SKILL.md만 raw 다운로드
```bash
mkdir -p ~/.claude/skills/skill-create-코어5
curl -L https://raw.githubusercontent.com/SUNWOONGKYU/skill-create/main/skill-create-%EC%BD%94%EC%96%B45/SKILL.md \
     -o ~/.claude/skills/skill-create-코어5/SKILL.md
```

## 설치 확인
```bash
ls ~/.claude/skills/ | grep skill-create-코어5
```
새 Claude Code 세션에서 `/skill-create-코어5 [만들 스킬 설명]`이 인식되면 정상. (실행 중이었다면 재시작.)

## 필수 동반 스킬 — mbo-천상 (공개명 mbo-skill)

이 스킬은 **`mbo-천상`(공개명 `mbo-skill`, 호출 `/mbo`)에 필수 의존**한다. Phase 2 목표서 양식·PO 승인 게이트·MBO 파일 저장·결과 보고가 전부 그 스킬에서 온다. 없으면 착수 전 자동 설치를 시도한다. SKILL.md 본문의 `mbo-천상`·`/mbo-천상` 표기는 전부 이 스킬을 가리킨다 — 공개 저장소·설치 폴더명은 `mbo-skill`·`mbo`, 실제 호출은 `/mbo`이다.

미리 설치해 두려면:
```bash
# Git Bash / macOS / Linux
mkdir -p ~/.claude/skills/mbo
curl -fsSL -o ~/.claude/skills/mbo/SKILL.md https://raw.githubusercontent.com/SUNWOONGKYU/mbo-skill/main/SKILL.md
```
```powershell
# Windows PowerShell
New-Item -ItemType Directory -Force "$HOME\.claude\skills\mbo" | Out-Null
Invoke-WebRequest -Uri https://raw.githubusercontent.com/SUNWOONGKYU/mbo-skill/main/SKILL.md -OutFile "$HOME\.claude\skills\mbo\SKILL.md"
```
저장소: [SUNWOONGKYU/mbo-skill](https://github.com/SUNWOONGKYU/mbo-skill)

## 검증 편제

Phase 5(설계서 확정)와 Phase 7(출하 검증) 두 곳에서 각 1회, 반드시 **다른 세션**이 검증한다(자기검증 금지).

- **작성자** — 이 스킬을 실행하는 Claude Code 세션 (Opus 5)
- **Phase 5 — 설계 검증**: V1(Claude Code Teammate, 제조 미참여 별도 세션·읽기전용, Sonnet 5)이 문서(설계서·관계도/흐름도·BOM)만 읽고 이진 체크리스트 12항목을 판정. 코드 실행 없음.
- **Phase 7 — 출하 검증**: V1(Sonnet 5, 5축 100점) + V2(Codex CLI, GPT-5.6 Sol, 탐지 실패 시 terra 1회 대체) — 미설치·인증 실패·할당량 소진 시 Opus 5 Teammate 폴백. "구현이 설계대로인가 + 실제로 도는가"만 검사(설계 적합성은 Phase 5에서 소진).

## 핵심 원칙 (8대 철칙)
1. 발굴물 무신뢰 — 공개 저장소도 통째 신뢰 금지
2. 부품 단위 선별
3. 운용 충돌 0건 — 타협 불가
4. 스무고개 항상 강제 (10라운드 기본)
5. MBO 승인 게이트
6. 자기검증 금지 — 별도 Verification Subagent
7. "curl 200 ≠ 동작함" — 사용자 화면 직접 확인
8. 자산화·운영까지가 완료

## 라이선스
[MIT](LICENSE) — 자유롭게 fork·수정·재배포 가능.

---
🤖 Generated and maintained with Claude Code.
