# JavaScript 클래스 (Class) 완벽 가이드

## 📚 출처 및 개요

**출처** : JavaScript 클래스 학습 자료

**주제** : ES6 클래스 문법, 생성자, 메서드, 필드, 정적 멤버

**학습 목표** : 클래스를 사용한 객체 지향 프로그래밍의 기초 이해

---

## 1. 클래스 기본 개념

### 1.1 클래스란?

**정의** : 클래스(Class)는 객체를 생성하기 위한 템플릿입니다. ES6에서 도입된 문법으로, 기존의 프로토타입 기반 상속을 보다 명확하고 간단한 문법으로 작성할 수 있게 해줍니다.

**특징** :

- Syntactic Sugar: 자바스크립트의 프로토타입 기반 구조를 클래스 문법으로 포장
- 다른 객체 지향 언어(Java, C++ 등)에 익숙한 개발자들을 위한 친숙한 문법 제공
- 내부적으로는 여전히 프로토타입 기반으로 동작

### 1.2 클래스 선언과 인스턴스 생성

**기본 문법** :

```jsx
class 클래스이름 {
  constructor(매개변수) {
    // 초기화 코드
  }

  메서드이름() {
    // 메서드 코드
  }
}
```

**사용 예시** :

```jsx
class YalcoChicken {
  constructor(name, no) {
    this.name = name;
    this.no = no;
  }

  introduce() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
}

const chain1 = new YalcoChicken("판교", 3);
const chain2 = new YalcoChicken("강남", 17);
const chain3 = new YalcoChicken("제주", 24);

console.log(chain1.introduce());
// 출력: "안녕하세요, 3호 판교점입니다!"
```

**언제 사용하는가** :

- 비슷한 구조를 가진 여러 객체를 생성할 때
- 코드의 재사용성과 유지보수성을 높이고 싶을 때
- 객체 지향 프로그래밍 패턴을 구현할 때

### 1.3 클래스 vs 생성자 함수

**차이점 1: 호이스팅**

```jsx
// ❌ 오류 발생
const chain1 = new YalcoChicken("판교", 3);

class YalcoChicken {
  constructor(name, no) {
    this.name = name;
    this.no = no;
  }
}
```

- 클래스는 호이스팅되지 않음 (정확히는 TDZ에 들어감)
- 선언 전에 사용 불가

**차이점 2: new 키워드 필수**

```jsx
// ❌ 오류 발생
const chain2 = YalcoChicken("강남", 17);

// ✅ 올바른 사용
const chain2 = new YalcoChicken("강남", 17);
```

- 클래스는 반드시 `new` 키워드와 함께 사용
- 생성자 함수는 `new` 없이 호출 시 오류 없이 `undefined` 반환

**차이점 3: 엄격 모드**

- 클래스 내부는 자동으로 엄격 모드(strict mode)가 적용됨

---

## 2. Constructor 메서드

### 2.1 Constructor의 역할

**정의** : `constructor`는 클래스의 인스턴스 객체를 생성하고 초기화하는 특별한 메서드입니다.

**특징** :

- 클래스에 하나만 존재 가능 (중복 시 오류)
- 인스턴스 생성 시 자동으로 호출됨
- 인자를 받아 프로퍼티를 초기화
- 다른 이름 사용 불가

### 2.2 Constructor 문법

**기본 사용** :

```jsx
class Person {
  constructor(name, age, married = false) {
    this.name = name;
    this.age = age;
    this.married = married;
  }
}

const person1 = new Person("박영희", 30, true);
const person2 = new Person("오동수", 18);

console.log(person1);
// Person { name: '박영희', age: 30, married: true }

console.log(person2);
// Person { name: '오동수', age: 18, married: false }
```

**언제 사용하는가** :

- 인스턴스 생성 시 초기값을 설정해야 할 때
- 매개변수를 받아 프로퍼티를 초기화할 때

### 2.3 Constructor 생략

**초기화가 필요 없는 경우** :

```jsx
class Empty {}

const empty = new Empty();
console.log(empty);
// Empty {}
```

- 인자가 없거나 초기화가 필요 없을 때 생략 가능

### 2.4 주의사항

⚠️ **값을 반환하지 말 것**

```jsx
// ❌ 잘못된 사용
class Wrong {
  constructor(name) {
    this.name = name;
    return { error: true }; // 반환하지 말 것
  }
}
```

- `constructor`는 암묵적으로 `this`를 반환
- 명시적으로 값을 반환하면 예상치 못한 동작 발생

---

## 3. 클래스의 메서드

### 3.1 메서드 정의

**기본 문법** :

```jsx
class Dog {
  bark() {
    return "멍멍";
  }
}

const badugi = new Dog();
console.log(badugi.bark());
// 출력: "멍멍"
```

**언제 사용하는가** :

- 인스턴스가 수행할 동작을 정의할 때
- 객체의 행동(behavior)을 구현할 때

### 3.2 메서드 vs 프로퍼티 함수

**클래스 메서드 (프로토타입에 저장)** :

```jsx
class Dog {
  bark() {
    return "멍멍";
  }
}

const badugi = new Dog();
console.log(badugi);
// Dog {} - bark는 프로토타입에 존재
```

**생성자 함수의 프로퍼티 함수** :

```jsx
function Dog2() {
  this.bark = function () {
    return "멍멍";
  };
}

const badugi2 = new Dog2();
console.log(badugi2);
// Dog2 { bark: [Function] } - bark가 인스턴스에 직접 존재
```

**차이점** :

- 클래스 메서드: 프로토타입에 한 번만 저장 (메모리 효율적)
- 프로퍼티 함수: 인스턴스마다 별도로 저장 (메모리 비효율적)

---

## 4. 필드 (Field)

### 4.1 필드란?

**정의** : 필드는 `constructor` 밖에서 `this.` 없이 인스턴스의 프로퍼티를 정의하는 문법입니다.

**특징** :

- ES2022에서 정식 표준으로 채택
- 이미 대부분의 최신 브라우저에서 지원
- Babel을 통해 이전 환경에서도 사용 가능

### 4.2 필드 사용 예시

**기본 사용** :

```jsx
class Slime {
  hp = 50;
  op = 4;

  attack(enemy) {
    enemy.hp -= this.op;
    this.hp += this.op / 4;
  }
}

const slime1 = new Slime();
const slime2 = new Slime();

console.log(slime1);
// Slime { hp: 50, op: 4 }

slime1.attack(slime2);

console.log(slime1);
// Slime { hp: 51, op: 4 }
console.log(slime2);
// Slime { hp: 46, op: 4 }
```

**언제 사용하는가** :

- 모든 인스턴스가 동일한 초기값을 가질 때
- `constructor`를 간결하게 유지하고 싶을 때
- 클래스의 구조를 한눈에 파악하고 싶을 때

### 4.3 필드와 Constructor 함께 사용

```jsx
class YalcoChicken {
  no = 0;
  menu = { 후라이드: 10000, 양념치킨: 12000 };

  constructor(name, no) {
    this.name = name;
    if (no) this.no = no;
  }

  introduce() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }

  order(name) {
    return `${this.menu[name]}원입니다.`;
  }
}

const chain0 = new YalcoChicken("(미정)");
console.log(chain0.introduce());
// "안녕하세요, 0호 (미정)점입니다!"

const chain1 = new YalcoChicken("판교", 3);
console.log(chain1.introduce());
// "안녕하세요, 3호 판교점입니다!"

chain1.menu["양념치킨"] = 13000;

console.log(chain0.order("양념치킨"));
// "12000원입니다."
console.log(chain1.order("양념치킨"));
// "13000원입니다."
```

**동작 방식** :

1. 필드로 기본값 설정
2. `constructor`에서 인자로 받은 값으로 덮어쓰기 가능
3. 각 인스턴스는 독립적인 프로퍼티 보유

---

## 5. 정적 (Static) 필드와 메서드

### 5.1 Static의 개념

**정의** : `static` 키워드를 사용하면 클래스 자체에 속하는 멤버를 정의할 수 있습니다. 인스턴스가 아닌 클래스 차원에서 호출됩니다.

**특징** :

- 인스턴스의 수와 관계없이 메모리 한 곳만 차지
- 인스턴스 없이 클래스 이름으로 직접 호출
- 정적 메서드에서는 정적 필드만 사용 가능

### 5.2 Static 사용 예시

```jsx
class YalcoChicken {
  // 정적 필드
  static brand = "얄코치킨";

  // 정적 메서드
  static contact() {
    return `${this.brand}입니다. 무엇을 도와드릴까요?`;
  }

  // 인스턴스 필드
  constructor(name, no) {
    this.name = name;
    this.no = no;
  }

  // 인스턴스 메서드
  introduce() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
}

console.log(YalcoChicken.brand);
// "얄코치킨"

console.log(YalcoChicken.contact());
// "얄코치킨입니다. 무엇을 도와드릴까요?"

const chain1 = new YalcoChicken("판교", 3);
console.log(chain1.introduce());
// "안녕하세요, 3호 판교점입니다!"
```

**언제 사용하는가** :

- 모든 인스턴스가 공유하는 정보를 저장할 때
- 유틸리티 함수를 클래스에 묶어서 관리할 때
- 인스턴스 생성 없이 사용할 기능을 구현할 때

### 5.3 Static 주의사항

⚠️ **정적 메서드에서 인스턴스 필드 접근 불가**

```jsx
class Example {
  instanceField = "instance";
  static staticField = "static";

  static staticMethod() {
    console.log(this.staticField); // ✅ 가능
    console.log(this.instanceField); // ❌ undefined
  }
}
```

---

## 6. 클래스의 본질

### 6.1 클래스는 함수

```jsx
class Dog {
  bark() {
    return "멍멍";
  }
}

console.log(typeof Dog);
// "function"
```

**특징** :

- 클래스는 특별한 종류의 함수
- `typeof` 연산자로 확인하면 `"function"` 반환

### 6.2 클래스는 일급 객체

```jsx
class Dog {
  bark() {
    return "멍멍";
  }
}

const 개 = Dog; // 변수에 할당 가능
const 바둑이 = new 개();

console.log(바둑이.bark());
// "멍멍"
```

**일급 객체의 특징** :

- 변수에 할당 가능
- 함수의 인자로 전달 가능
- 함수의 반환값으로 사용 가능

---

## 📝 핵심 요약

### 클래스 기본

- 클래스는 객체 생성을 위한 템플릿이며, 프로토타입 기반 상속의 문법적 설탕(Syntactic Sugar)
- 호이스팅되지 않으며, 반드시 `new` 키워드와 함께 사용해야 함
- 내부적으로 엄격 모드가 자동 적용됨

### Constructor

- 인스턴스를 생성하고 초기화하는 특별한 메서드
- 클래스당 하나만 존재 가능하며, 기본값 사용 가능
- 필요 없을 시 생략 가능하며, 암묵적으로 `this` 반환

### 메서드

- 프로토타입에 저장되어 메모리 효율적
- 인스턴스의 동작(behavior)을 정의

### 필드

- `constructor` 밖에서 프로퍼티 정의 가능
- ES2022 표준이며, 코드의 가독성 향상

### Static

- 클래스 자체에 속하는 멤버
- 인스턴스 없이 클래스 이름으로 직접 호출
- 정적 메서드는 정적 필드만 사용 가능

### 클래스의 본질

- 클래스는 함수이며 일급 객체
- 변수에 할당하고 전달 가능

---

## 🎯 복습 퀴즈

### 문제 1

다음 중 클래스에 대한 설명으로 틀린 것은?

1. 클래스는 호이스팅되지 않는다
2. 클래스는 new 키워드 없이도 호출할 수 있다
3. 클래스는 프로토타입 기반의 문법적 설탕이다
4. 클래스 내부는 자동으로 엄격 모드가 적용된다
5. 클래스는 typeof 연산 시 "function"을 반환한다

**정답** : 2번

**해설** : 클래스는 반드시 `new` 키워드와 함께 사용해야 합니다. `new` 없이 호출하면 오류가 발생합니다. 이는 생성자 함수와의 주요 차이점 중 하나입니다.

---

### 문제 2

다음 코드의 실행 결과는?

```jsx
class Counter {
  count = 0;

  increment() {
    this.count++;
  }
}

const c1 = new Counter();
const c2 = new Counter();

c1.increment();
c1.increment();
c2.increment();

console.log(c1.count, c2.count);
```

1. 0 0
2. 1 1
3. 2 1
4. 3 3
5. 오류 발생

**정답** : 3번

**해설** : 필드로 정의된 `count`는 각 인스턴스마다 독립적으로 생성됩니다. `c1`은 2번 증가하여 2가 되고, `c2`는 1번 증가하여 1이 됩니다.

---

### 문제 3

다음 중 constructor 메서드에 대한 설명으로 옳은 것은?

1. 클래스에 여러 개 정의할 수 있다
2. 반드시 값을 명시적으로 반환해야 한다
3. 다른 이름(예: init)으로 변경할 수 있다
4. 생략 가능하다
5. 인스턴스 생성 후에 수동으로 호출해야 한다

**정답** : 4번

**해설** : `constructor`는 초기화가 필요 없거나 인자가 없을 때 생략 가능합니다. 클래스당 하나만 존재할 수 있으며, 이름을 변경할 수 없고, 인스턴스 생성 시 자동으로 호출되며, 암묵적으로 `this`를 반환합니다.

---

### 문제 4

다음 코드에서 메모리를 가장 효율적으로 사용하는 방법은?

```jsx
class Product {
  // 방법을 선택하세요
}

const p1 = new Product();
const p2 = new Product();
const p3 = new Product();
```

1. `constructor` 내부에서 `this.method = function() {}`로 정의
2. 클래스 메서드로 정의
3. 필드로 화살표 함수 정의
4. 정적 메서드로 정의
5. 모두 동일한 메모리 사용

**정답** : 2번

**해설** : 클래스 메서드는 프로토타입에 한 번만 저장되어 모든 인스턴스가 공유합니다. 반면 `constructor`나 필드에서 함수를 정의하면 각 인스턴스마다 별도로 저장되어 메모리를 더 많이 사용합니다.

---

### 문제 5

다음 코드의 실행 결과는?

```jsx
class Company {
  static employees = 0;

  constructor(name) {
    this.name = name;
    Company.employees++;
  }

  static getCount() {
    return `총 직원 수: ${this.employees}명`;
  }
}

const e1 = new Company("김철수");
const e2 = new Company("이영희");
const e3 = new Company("박민수");

console.log(Company.getCount());
```

1. 총 직원 수: 0명
2. 총 직원 수: 1명
3. 총 직원 수: 3명
4. undefined
5. 오류 발생

**정답** : 3번

**해설** : `static` 필드는 클래스 차원에서 하나만 존재하며, 모든 인스턴스가 공유합니다. 각 인스턴스 생성 시 `Company.employees`가 증가하므로 3개의 인스턴스 생성 후 값은 3이 됩니다.

---

### 문제 6

다음 중 정적(static) 메서드에서 할 수 없는 작업은?

```jsx
class Example {
  instanceField = "instance";
  static staticField = "static";

  static staticMethod() {
    // 여기서 할 수 없는 작업은?
  }
}
```

1. 정적 필드에 접근
2. 다른 정적 메서드 호출
3. 인스턴스 필드에 접근
4. this 키워드 사용
5. 값을 반환

**정답** : 3번

**해설** : 정적 메서드는 인스턴스와 독립적으로 동작하므로 인스턴스 필드나 메서드에 접근할 수 없습니다. `this`는 클래스 자체를 가리키므로 정적 멤버만 접근 가능합니다.

---

### 문제 7

다음 코드의 문제점은?

```jsx
const c = new Car("Tesla");

class Car {
  constructor(brand) {
    this.brand = brand;
  }
}
```

1. constructor에서 return이 없음
2. 클래스가 호이스팅되지 않아 선언 전 사용 불가
3. new 키워드 사용이 잘못됨
4. 필드 정의가 없음
5. 문제없음, 정상 실행됨

**정답** : 2번

**해설** : 클래스는 호이스팅되지 않으므로(정확히는 TDZ에 들어가므로) 선언 전에 사용할 수 없습니다. 클래스 선언 이후에 인스턴스를 생성해야 합니다.

---

### 문제 8

다음 코드의 실행 결과는?

```jsx
class Animal {
  sound = "...";

  makeSound() {
    return this.sound;
  }
}

class Dog extends Animal {
  sound = "멍멍";
}

const dog = new Dog();
console.log(dog.makeSound());
```

1. ...
2. 멍멍
3. undefined
4. 오류 발생
5. Animal

**정답** : 2번

**해설** : 비록 상속 내용이 본문에 없지만, 필드는 각 클래스에서 정의된 값으로 초기화됩니다. `Dog` 클래스에서 `sound` 필드를 '멍멍'으로 재정의했으므로, 상속받은 `makeSound()` 메서드는 '멍멍'을 반환합니다.

---

## ✅ 학습 체크리스트

학습을 완료한 항목에 체크하세요.

- [ ] 클래스의 기본 문법을 이해하고 작성할 수 있다
- [ ] 클래스와 생성자 함수의 차이점을 설명할 수 있다
- [ ] 클래스가 호이스팅되지 않는 이유를 이해한다
- [ ] `constructor` 메서드의 역할과 특징을 안다
- [ ] `constructor`에서 기본값을 설정할 수 있다
- [ ] `constructor`를 생략할 수 있는 경우를 안다
- [ ] 클래스 메서드를 정의하고 사용할 수 있다
- [ ] 메서드가 프로토타입에 저장되는 것을 이해한다
- [ ] 필드(field) 문법을 사용하여 프로퍼티를 정의할 수 있다
- [ ] 필드와 `constructor`를 함께 사용할 수 있다
- [ ] 정적(static) 필드와 메서드의 개념을 이해한다
- [ ] 정적 멤버를 클래스 이름으로 호출할 수 있다
- [ ] 정적 메서드의 제약사항을 이해한다
- [ ] 클래스가 함수이자 일급 객체임을 이해한다
- [ ] 클래스를 변수에 할당하고 전달할 수 있다

---

## 💻 연습문제

### 문제 1: 기본 클래스 구현

**문제** : 다음 요구사항을 만족하는 `Book` 클래스를 작성하세요.

**요구사항** :

- 제목(title), 저자(author), 페이지 수(pages) 프로퍼티를 가짐
- `getInfo()` 메서드는 "제목: [title], 저자: [author]" 형식의 문자열 반환
- `isLongBook()` 메서드는 페이지가 300 이상이면 true, 아니면 false 반환

  **기본 코드** :

```jsx
class Book {
  // 여기에 코드 작성
}

// 테스트 코드
const book1 = new Book("클린 코드", "로버트 마틴", 584);
const book2 = new Book("JavaScript 기초", "김코딩", 250);

console.log(book1.getInfo());
console.log(book1.isLongBook());
console.log(book2.isLongBook());
```

**정답** :

```jsx
class Book {
  constructor(title, author, pages) {
    this.title = title;
    this.author = author;
    this.pages = pages;
  }

  getInfo() {
    return `제목: ${this.title}, 저자: ${this.author}`;
  }

  isLongBook() {
    return this.pages >= 300;
  }
}

// 테스트 코드
const book1 = new Book("클린 코드", "로버트 마틴", 584);
const book2 = new Book("JavaScript 기초", "김코딩", 250);

console.log(book1.getInfo());
// "제목: 클린 코드, 저자: 로버트 마틴"

console.log(book1.isLongBook());
// true

console.log(book2.isLongBook());
// false
```

**해설** :

- `constructor`에서 세 개의 매개변수를 받아 인스턴스 프로퍼티로 저장
- `getInfo()`는 템플릿 리터럴을 사용하여 정보를 반환
- `isLongBook()`는 조건 연산을 통해 boolean 값 반환

---

### 문제 2: 필드(Field) 활용

**문제** : 다음 요구사항을 만족하는 `BankAccount` 클래스를 작성하세요.

**요구사항** :

- 필드를 사용하여 `balance`를 0으로 초기화
- `accountHolder` 프로퍼티는 생성자에서 받아 설정
- `deposit(amount)` 메서드로 입금 (잔액 증가)
- `withdraw(amount)` 메서드로 출금 (잔액이 부족하면 "잔액 부족" 반환)
- `getBalance()` 메서드로 현재 잔액 반환

  **기본 코드** :

```jsx
class BankAccount {
  // 여기에 코드 작성
}

// 테스트 코드
const account = new BankAccount("홍길동");
account.deposit(10000);
account.deposit(5000);
console.log(account.getBalance());
account.withdraw(7000);
console.log(account.getBalance());
console.log(account.withdraw(10000));
```

**정답** :

```jsx
class BankAccount {
  balance = 0;

  constructor(accountHolder) {
    this.accountHolder = accountHolder;
  }

  deposit(amount) {
    this.balance += amount;
    return `${amount}원 입금되었습니다.`;
  }

  withdraw(amount) {
    if (this.balance < amount) {
      return "잔액 부족";
    }
    this.balance -= amount;
    return `${amount}원 출금되었습니다.`;
  }

  getBalance() {
    return `현재 잔액: ${this.balance}원`;
  }
}

// 테스트 코드
const account = new BankAccount("홍길동");
account.deposit(10000);
account.deposit(5000);
console.log(account.getBalance());
// "현재 잔액: 15000원"

account.withdraw(7000);
console.log(account.getBalance());
// "현재 잔액: 8000원"

console.log(account.withdraw(10000));
// "잔액 부족"
```

**해설** :

- 필드 문법으로 `balance = 0` 초기화
- `deposit`은 잔액을 증가시킴
- `withdraw`는 조건문으로 잔액 확인 후 출금 처리
- 각 메서드는 적절한 메시지를 반환

---

### 문제 3: 정적(Static) 멤버 활용

**문제** : 다음 요구사항을 만족하는 `Student` 클래스를 작성하세요.

**요구사항** :

- 정적 필드 `studentCount`를 0으로 초기화
- 생성자에서 이름(name)과 학년(grade)을 받음
- 인스턴스 생성 시마다 `studentCount` 증가
- 정적 메서드 `getTotalStudents()`는 전체 학생 수 반환
- 인스턴스 메서드 `introduce()`는 "이름: [name], 학년: [grade]" 반환

  **기본 코드** :

```jsx
class Student {
  // 여기에 코드 작성
}

// 테스트 코드
const s1 = new Student("김철수", 1);
const s2 = new Student("이영희", 2);
const s3 = new Student("박민수", 1);

console.log(Student.getTotalStudents());
console.log(s1.introduce());
console.log(s2.introduce());
```

**정답** :

```jsx
class Student {
  static studentCount = 0;

  constructor(name, grade) {
    this.name = name;
    this.grade = grade;
    Student.studentCount++;
  }

  static getTotalStudents() {
    return `전체 학생 수: ${this.studentCount}명`;
  }

  introduce() {
    return `이름: ${this.name}, 학년: ${this.grade}학년`;
  }
}

// 테스트 코드
const s1 = new Student("김철수", 1);
const s2 = new Student("이영희", 2);
const s3 = new Student("박민수", 1);

console.log(Student.getTotalStudents());
// "전체 학생 수: 3명"

console.log(s1.introduce());
// "이름: 김철수, 학년: 1학년"

console.log(s2.introduce());
// "이름: 이영희, 학년: 2학년"
```

**해설** :

- `static studentCount`는 클래스 차원에서 하나만 존재
- `constructor`에서 `Student.studentCount++`로 증가
- 정적 메서드는 `Student.getTotalStudents()`로 호출
- 인스턴스 메서드는 각 인스턴스의 정보를 반환

---

### 문제 4: 종합 응용

**문제** : 다음 요구사항을 만족하는 `Product` 클래스를 작성하세요.

**요구사항** :

- 필드로 `discount = 0` 초기화
- 생성자에서 상품명(name), 가격(price) 받음
- `setDiscount(percent)` 메서드로 할인율 설정 (0~100 사이 값)
- `getFinalPrice()` 메서드로 할인 적용된 최종 가격 반환
- 정적 필드 `taxRate = 0.1` (세율 10%)
- 정적 메서드 `calculateTax(price)`로 세금 계산

  **기본 코드** :

```jsx
class Product {
  // 여기에 코드 작성
}

// 테스트 코드
const laptop = new Product("노트북", 1000000);
laptop.setDiscount(20);

console.log(laptop.getFinalPrice());
console.log(Product.calculateTax(laptop.getFinalPrice()));
```

**정답** :

```jsx
class Product {
  discount = 0;
  static taxRate = 0.1;

  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  setDiscount(percent) {
    if (percent >= 0 && percent <= 100) {
      this.discount = percent;
    }
  }

  getFinalPrice() {
    return this.price * (1 - this.discount / 100);
  }

  static calculateTax(price) {
    return price * this.taxRate;
  }
}

// 테스트 코드
const laptop = new Product("노트북", 1000000);
laptop.setDiscount(20);

console.log(laptop.getFinalPrice());
// 800000

console.log(Product.calculateTax(laptop.getFinalPrice()));
// 80000
```

**해설** :

- 필드와 정적 필드를 모두 활용
- `setDiscount`는 유효성 검사 포함
- `getFinalPrice`는 할인율을 계산하여 최종 가격 반환
- 정적 메서드는 세율을 적용하여 세금 계산
- 인스턴스 메서드와 정적 메서드를 조합하여 사용

---

### 문제 5: 실전 응용 - 게임 캐릭터

**문제** : RPG 게임의 캐릭터를 표현하는 `Character` 클래스를 작성하세요.

**요구사항** :

- 필드: `level = 1`, `exp = 0`
- 생성자: 이름(name), HP(hp), 공격력(attack)
- `attackEnemy(enemy)` 메서드: 상대방 HP를 자신의 공격력만큼 감소, 자신은 경험치 10 획득
- `gainExp(amount)` 메서드: 경험치 획득, 100 이상이면 레벨업 (레벨+1, 경험치-100, HP+20, 공격력+5)
- `getStatus()` 메서드: 모든 스탯 정보를 문자열로 반환
- 정적 필드 `characterCount = 0`: 생성된 캐릭터 수
- 정적 메서드 `getCharacterCount()`: 전체 캐릭터 수 반환

  **기본 코드** :

```jsx
class Character {
  // 여기에 코드 작성
}

// 테스트 코드
const hero = new Character("용사", 100, 20);
const enemy = new Character("슬라임", 50, 5);

console.log(hero.getStatus());
hero.attackEnemy(enemy);
hero.gainExp(95);
console.log(hero.getStatus());
console.log(enemy.getStatus());
console.log(Character.getCharacterCount());
```

**정답** :

```jsx
class Character {
  level = 1;
  exp = 0;
  static characterCount = 0;

  constructor(name, hp, attack) {
    this.name = name;
    this.hp = hp;
    this.attack = attack;
    Character.characterCount++;
  }

  attackEnemy(enemy) {
    enemy.hp -= this.attack;
    this.gainExp(10);
    return `${this.name}이(가) ${enemy.name}을(를) 공격했습니다!`;
  }

  gainExp(amount) {
    this.exp += amount;
    if (this.exp >= 100) {
      this.level++;
      this.exp -= 100;
      this.hp += 20;
      this.attack += 5;
      return `레벨업! 현재 레벨: ${this.level}`;
    }
  }

  getStatus() {
    return `[${this.name}] Lv.${this.level} | HP: ${this.hp} | 공격력: ${this.attack} | 경험치: ${this.exp}/100`;
  }

  static getCharacterCount() {
    return `생성된 캐릭터 수: ${this.characterCount}`;
  }
}

// 테스트 코드
const hero = new Character("용사", 100, 20);
const enemy = new Character("슬라임", 50, 5);

console.log(hero.getStatus());
// "[용사] Lv.1 | HP: 100 | 공격력: 20 | 경험치: 0/100"

hero.attackEnemy(enemy);
hero.gainExp(95);
// 레벨업 발생 (경험치 10 + 95 = 105)

console.log(hero.getStatus());
// "[용사] Lv.2 | HP: 120 | 공격력: 25 | 경험치: 5/100"

console.log(enemy.getStatus());
// "[슬라임] Lv.1 | HP: 30 | 공격력: 5 | 경험치: 0/100"

console.log(Character.getCharacterCount());
// "생성된 캐릭터 수: 2"
```

**해설** :

- 필드로 레벨과 경험치 초기화
- `attackEnemy`는 상대방 공격 후 자신의 경험치 획득
- `gainExp`는 경험치를 더하고 레벨업 조건 확인
- 레벨업 시 모든 스탯 증가
- 정적 멤버로 전체 캐릭터 수 관리
- 여러 메서드가 유기적으로 연결되어 동작

---

## 🎓 학습을 마치며

이 문서를 통해 JavaScript 클래스의 기본 개념부터 실전 활용까지 학습했습니다.

**다음 학습 권장 사항** :

- 상속(Inheritance)과 `extends` 키워드
- `super` 키워드와 부모 클래스 참조
- 접근자 프로퍼티 (getter/setter)
- Private 필드와 메서드
- 클래스를 활용한 디자인 패턴

  **복습 방법** :

1. 체크리스트의 모든 항목을 확인
2. 퀴즈를 다시 풀어보기
3. 연습문제를 코드 없이 직접 작성해보기
4. 실제 프로젝트에 클래스 적용해보기

화이팅! 💪
