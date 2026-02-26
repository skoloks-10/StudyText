# 💻 JavaScript 학습 기록

> 웹 개발의 핵심인 JavaScript를 기초부터 고급까지 체계적으로 학습하는 과정입니다.

## 📖 학습 로드맵

### 📌 기초 개념 (1~4강)
- **001. 콘솔 출력과 변수, 상수** - console.log(), var/let/const, 메모리 개념
- **002. 자료형** - String, Number, Boolean, Null, Undefined, Object, Symbol
- **003. 연산자** - 산술, 할당, 비교 연산자
- **004. 불리언과 관련 연산자** - 논리 연산자(AND, OR, NOT), 삼항 연산자

### 🔄 제어문과 함수 (5~8강)
- **006. 제어문** - if/else, switch/case, 반복문 (for, while, do-while)
- **007. 함수** - 함수 선언, 호출, 반환, 함수 표현식
- **008. 매개변수와 함수 활용** - 가변 인자, 기본값, Rest 문법
- **005. 연산자, 객체, 배열, 스코프** - 복합 개념 심화

### 📦 객체와 배열 (9~10강)
- **009. 객체와 생성자 함수** - 객체 리터럴, 생성자 함수, this 바인딩
- **010. 클래스와 객체활용** - ES6 클래스, 상속, 캡슐화

### 🛠️ 내장 객체와 메서드 (11~12강)
- **011. 전역 객체와 표준 빌트인 객체** - Global, Object, Array, String 객체
- **012. Number, Math, Date 객체** - 숫자/수학/날짜 관련 메서드

### 🔢 배열 고급 (13~15강)
- **013. 배열** - 배열 기초, 배열 메서드 (push, pop, shift, unshift)
- **014. 고차함수 메서드** - map(), filter(), reduce(), forEach() 등
- **015. 배열 스프레드 & 디스트럭처링 + ES14 배열 메서드** - 스프레드 문법, 비구조화 할당

### 🎯 객체와 JSON (16~17강)
- **016. 객체 깊게 배우기, JSON** - 객체 메서드, JSON 변환
- **017. 진법 & BigInt, Symbol, Set, Map** - 고급 자료형

### 🔁 이터러블과 제너레이터 (18강)
- **018. 이터러블, 제너레이터** - for...of, Iterator 프로토콜, Generator 함수

### ⚠️ 에러 처리와 고급 개념 (19~20강)
- **019. 에러처리, var, 엄격모드, 옵셔널 체이닝** - try/catch, var의 문제점, strict mode
- **020. 렉시컬 스코프와 클로저, this 바인딩** - 스코프 체인, 클로저, this 바인딩 규칙

### 🔗 프로토타입과 비동기 (21~22강)
- **021. 프로토타입 & 비동기** - 프로토타입 기반 상속, 콜백 기초
- **022. Promise, async, await, Fetch API** - Promise, async/await, HTTP 통신

### 🚀 웹 개발 실무 (23~26강)
- **023. HTML에 로드, 모듈과 라이브러리, 웹팩, 바벨** - 스크립트 로드, ES6 모듈, 번들링 및 트랜스파일
- **024. JSDoc, 디버깅, DOM** - 코드 문서화, 디버깅 기법, DOM 개념
- **025. 요소 선택과 탐색, 조작** - querySelector, DOM 탐색, 요소 생성/수정
- **026. DOM 이벤트** - 이벤트 리스너, 이벤트 객체, 이벤트 위임

---

## 🎯 핵심 학습 내용

| 레벨 | 주제 | 핵심 개념 |
|------|------|---------|
| **기초** | 문법 | 변수, 자료형, 연산자, 제어문 |
| **초급** | 함수와 스코프 | 함수, 클로저, 스코프 체인 |
| **중급** | 객체와 배열 | 객체 지향, 배열 메서드, 고차함수 |
| **중상** | 비동기 처리 | Promise, async/await, Fetch API |
| **고급** | 프로토타입과 DOM | 프로토타입 상속, DOM 조작, 이벤트 |

---

## 💡 자주 사용하는 코드 패턴

```javascript
// 변수 선언
const name = "John";      // 상수 (권장)
let age = 25;             // 변수
// var count = 0;         // 예전 방식 (피하기)

// 배열 고차함수
const numbers = [1, 2, 3, 4, 5];
numbers.map(n => n * 2);           // [2, 4, 6, 8, 10]
numbers.filter(n => n > 2);        // [3, 4, 5]
numbers.reduce((acc, n) => acc + n, 0);  // 15

// 구조 분해
const { name, age } = person;
const [first, second] = array;

// Promise와 async/await
async function fetchData() {
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
}

// DOM 조작
const element = document.querySelector('.selector');
element.addEventListener('click', (e) => {
  e.target.classList.add('active');
});

// 클래스 정의
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hello, ${this.name}!`;
  }
}
```

---

## 🛠️ 개발 환경 설정

### 필수 도구
- **에디터**: VS Code 또는 Cursor
- **런타임**: Node.js (로컬 테스트)
- **브라우저 개발자 도구**: F12 (콘솔, 디버거)

### 확장 프로그램
- Code Runner - JavaScript 빠른 실행
- ES7+ React/Redux/React-Native snippets - 스니펫
- Prettier - 코드 포매팅

---

## 📚 학습 방법

1. **순차 학습**: 001번부터 순서대로 학습
2. **개념 이해 > 코드 작성**: 각 개념을 이해한 후 코드로 직접 구현
3. **실전 프로젝트**: 배운 내용을 활용해 작은 프로젝트 제작
4. **복습 계획**:
   - 1주일 후: 어려웠던 개념 복습
   - 1달 후: 전체 언어 문법 복습

---

## 🎓 실무 학습 경로

### Phase 1: 기초 다지기 (001~010강)
- JavaScript 문법 완전 이해
- 함수와 객체 지향 개념 숙달

### Phase 2: 고급 개념 학습 (011~022강)
- 내장 객체와 메서드 활용
- 비동기 프로그래밍 마스터

### Phase 3: 웹 개발 실무 (023~026강)
- DOM 조작과 이벤트 처리
- 번들링과 모듈 시스템 이해

### Phase 4: 실전 프로젝트
- React/Vue 등 프레임워크 학습 준비
- 풀스택 개발 능력 구축

---

## 📖 추가 학습 자료

- **모던 JS 딥 다이브**: JavaScript 심화 학습서
- MDN Web Docs: https://developer.mozilla.org/
- JavaScript.info: https://javascript.info/

---

**마지막 업데이트**: 2026-02-26

