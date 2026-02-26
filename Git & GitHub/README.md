# 🌳 Git & GitHub 학습 기록

> 버전 관리 시스템 Git과 협업 플랫폼 GitHub의 모든 것을 배우는 과정입니다.

## 📖 학습 로드맵

### 🔧 기초 설정 및 기본 개념
- **001. Git 초기 설정** - Windows 환경에서의 Git, SourceTree, Cursor 설치 및 설정
- **002. Git 커밋과 되돌리기** - 기본 커밋 작업과 변경사항 복구 방법
- **003. 브랜치** - 브랜치 생성, 전환, 병합의 기초

### 📱 GitHub 연동 및 협업
- **004. GitHub 시작하기** - 원격 저장소 생성 및 로컬-원격 동기화
- **011. 깃헙 잘 사용하기** - Issue, Pull Request, Collaboration 활용법

### 🔍 심화 개념
- **005. Git 보다 깊이 알기** - Git의 내부 동작 원리와 고급 개념
- **006. 커밋 관리** - 커밋 히스토리 정리 및 관리 전략
- **007. 변경사항 관리 & 태그** - Stash, Tag를 활용한 변경사항 관리
- **008. Branch 심화** - 고급 브랜치 전략 (Rebase, Merge 전략)

### 🛠️ 고급 기능
- **009. 분석과 디버깅** - Git blame, bisect를 통한 문제 분석
- **010. Git Hook & Worktree** - 자동화 및 다중 작업 트리 관리

---

## 🎯 학습 포인트

| 주제 | 핵심 개념 |
|------|----------|
| **버전 관리** | Commit, Log, Diff, Revert |
| **브랜칭 전략** | Branch, Merge, Rebase, Conflict 해결 |
| **원격 저장소** | Push, Pull, Fetch, Remote |
| **협업** | Pull Request, Code Review, Collaboration |
| **고급 기능** | Hook, Worktree, Bisect, Blame |

---

## 💡 실무에서 자주 사용하는 커맨드

```bash
# 초기 설정
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 기본 작업
git add .
git commit -m "commit message"
git push origin branch-name
git pull origin branch-name

# 브랜치 관리
git branch
git checkout -b new-branch
git merge branch-name

# 변경사항 임시 보관
git stash
git stash pop

# 커밋 히스토리 확인
git log --oneline --graph --all
git show commit-hash
```

---

## 📚 학습 방법

1. **순서대로 진행**: 001번부터 순차적으로 학습하되, 필요시 심화 강의부터 시작 가능
2. **실습 중심**: 각 개념을 학습한 후 로컬 저장소에서 직접 실습
3. **반복 학습**: 1주일 후 어려웠던 부분 복습, 1달 후 전체 복습

---

**마지막 업데이트**: 2026-02-26

