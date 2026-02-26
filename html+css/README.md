# 🎨 HTML + CSS 학습 기록

> 웹 개발의 기초인 마크업과 스타일링을 완벽하게 학습하는 과정입니다.

## 📖 학습 로드맵

### 🏗️ HTML 기초
- **001. 기초태그** - HTML 문서 구조, 제목/문단, 개발 환경 설정 (VS Code, Live Server)
- **002. 기초태그2** - 추가 기본 태그 및 시맨틱 요소
- **003. 폼 요소** - `<form>`, `<input>`, `<select>` 등 사용자 입력 처리
- **008. HTML 문서구조와 메타데이터** - `<meta>`, `<title>`, `<head>` 태그의 역할

### 🎨 CSS 기초와 선택자
- **004. CSS 적용 방법과 선택자** - Inline, Internal, External CSS 및 기본 선택자
- **010. CSS 선택자 심화 및 스타일링** - 고급 선택자 (Pseudo-class, Pseudo-element)
- **005. CSS 텍스트 및 스타일링** - 폰트, 텍스트 스타일, 색상 적용

### 📦 CSS 레이아웃과 박스 모델
- **006. CSS 박스 모델과 레이아웃** - Margin, Padding, Border, Position
- **007. CSS 요소 숨김과 Flex 레이아웃** - Display 속성, Flexbox를 이용한 반응형 디자인
- **011. 테이블, 텍스트, Float, Grid 레이아웃** - CSS Grid, Float를 이용한 다양한 레이아웃 기법

### 🎬 고급 CSS
- **009. CSS 명명 규칙과 미디어 활용** - BEM, SMACSS 등 CSS 네이밍 컨벤션
- **012. CSS 변형, 애니메이션 및 반응형 웹** - Transform, Animation, Media Query를 활용한 반응형 웹 디자인
- **013. 기타속성, 프레임워크와 라이브러리** - Bootstrap, Tailwind 등 CSS 프레임워크

### 💼 실전 프로젝트
- **파이널프로젝트/** - 학습한 모든 개념을 종합한 실제 웹페이지 프로젝트

---

## 🎯 핵심 학습 내용

| 카테고리 | 주요 개념 |
|---------|---------|
| **HTML 기초** | 시맨틱 마크업, 접근성(Accessibility), SEO |
| **CSS 선택자** | 기본/고급 선택자, 특이도(Specificity), 캐스케이드(Cascade) |
| **박스 모델** | Margin, Padding, Border, Box-sizing |
| **레이아웃** | Flexbox, CSS Grid, Float, Position |
| **반응형 디자인** | Media Query, 모바일 우선 설계, 뷰포트 설정 |
| **애니메이션** | Transform, Transition, Animation |

---

## 💻 자주 사용하는 CSS 코드 스니펫

```css
/* Flexbox 레이아웃 */
.flex-container {
  display: flex;
  justify-content: center;    /* 가로 정렬 */
  align-items: center;        /* 세로 정렬 */
  gap: 20px;
}

/* CSS Grid 레이아웃 */
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

/* 반응형 웹 - 모바일 우선 */
@media (min-width: 768px) {
  /* 태블릿 이상 */
}

@media (min-width: 1024px) {
  /* 데스크톱 */
}

/* 기본 box-sizing 설정 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* 애니메이션 */
@keyframes slideIn {
  from { transform: translateX(-100%); }
  to { transform: translateX(0); }
}

.element {
  animation: slideIn 0.3s ease-out;
}
```

---

## 🛠️ 개발 환경 설정

### 필수 도구
- **에디터**: VS Code
- **확장 프로그램**:
  - Live Server - HTML 실시간 미리보기
  - HTML Snippets - HTML 자동완성
  - CSS Peek - CSS 클래스 추적

### Emmet 단축키 활용
```
! + Tab → HTML 기본 구조 자동 생성
div.class-name + Tab → 클래스가 있는 div 생성
ul>li*3 + Tab → 자동 구조 생성
```

---

## 📚 학습 방법

1. **순차 학습**: 001번부터 차례대로 진행 (CSS 선택자는 심화 강의가 있으므로 기초 후 심화 학습)
2. **실습 중심**: 각 강의마다 간단한 예제 프로젝트 제작
3. **최종 프로젝트**: 파이널프로젝트에서 배운 모든 내용을 종합하여 실제 웹페이지 구현
4. **복습 계획**:
   - 1주일 후: 어려웠던 레이아웃 개념 복습
   - 1달 후: 전체 포트폴리오 재점검

---

## 🎓 다음 단계

- JavaScript를 배워 상호작용하는 웹페이지 제작
- CSS 프레임워크 (Bootstrap, Tailwind) 심화 학습
- 반응형 디자인 패턴 실습

---

**마지막 업데이트**: 2026-02-26

