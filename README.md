# skill-create-코어5

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
