# 📌Question

(김규)

### Q1) '이름 기반 구조 분해'가 도입된다면 많이 쓰일까요? (p.413 관련)

**A)김세진**

```kotlin
// 이름 기반 구조 분해
val (email = email, username = username) = user

// 프로퍼티 접근
val email = user.email
val username = user.username
```

---

### Q2) `lazy` 는 어떤 방식으로 thread-safe를 보장할까요? (p.418 관련)

**A)김승수**

- 답변...

---

(김세진)

### Q1) += 는 mutable 객체와 immutable 객체에서 어떻게 다르게 동작할까요?

**A)김규**

- mutable
  - 객체 자체는 변하지 않고, 내부 값을 직접 바꿈
  - `plusAssign` 사용
- immutable
  - 연산 결과를 새로운 객체로 만든 후, 변수에 다시 할당
  - `var` 일 경우에만 사용 가능
  - `plus` 사용

---
    
### Q2) Kotlin은 왜 operator 키워드를 강제할까요?

**A)김승수**


- 답변...

---

(김승수)

### Q1) 복합 대입 연산자(+=)를 사용할 때, plus와 plusAssign이 동시에 정의되어 있다면 어떤 일이 발생하며 이를 방지하려면 어떻게 해야 할까요?

**A)김세진**


- 답변...

---
    
### Q2) 동등성 비교(==)를 위한 equals 함수를 오버라이딩할 때, 왜 operator 키워드를 붙이지 않아도 될까요?

**A)김규**

- `Any`에 이미 `operator fun equals`가 정의되어 있기 때문에 override 만 가능
- 상속받은 함수가 확장 함수보다 우선순위가 높아서 `equals`는 확장함수로도 만들 수 없음

+ interface 에서는?
  - interface 의 `plus` 같은 메서드를 구현할 때 구현체에서 `operator fun` 으로 할지 말지는 선택사항
  - interface 에 operator로 정의되어 있었다면 필수지만, 그렇지 않은 경우에는 구현체에게 선택권한이 있음
  - 일관성 유지를 위해서는 인터페이스 자체에 붙이거나 말거나 선택하는 것이 낫다고 생각합니다

