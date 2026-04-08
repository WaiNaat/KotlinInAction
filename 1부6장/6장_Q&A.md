# 📌Question

(김규)

### Q1) `windowed`, `chunked`, `zip` 은 List처럼 명시적인 순서가 있는 컬렉션에만 가능한 것일까요? (p.299 관련)

**A) 김승수**

- 답변...

---

### Q2) 무한 시퀀스에 `toList()` 적용이 가능할까요? (p.310 관련)

**A) 김세진**

- 문법적으로는 가능하지만, 비정상 종료나 OOM 메모리 문제가 발생할 수 있음
- `toList()`는 **최종 연산(Terminal Operation)**이며, 시퀀스의 모든 요소를 소비하여 리스트로 만들려고 시도합니다.
- 무한 시퀀스는 끝이 없으므로 `toList()`는 계속해서 다음 요소를 찾고, 메모리는 가득 차 결국 `OutOfMemoryError`가 발생하거나 CPU가 무한 루프에 빠집니다.

```kotlin
val infiniteStep = generateSequence(1) { it + 1 }
val stopPlease = infiniteStep.toList()  //무한 시퀀스

// 반드시 take() 같은 함수로 제한을 두어야 합니다.
val finiteList = infiniteStep.take(10).toList() 
println(finiteList) // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

---

(김세진)

### Q1) groupBy 와 associateBy 차이점에 대해 설명

**A) 김승수**

- 답변...

---
    
### Q2) Sequence가 더 좋으면, 왜 Kotlin은 Sequence를 기본으로 안 만들었을까?

**A) 김규**
- sequence 는 iterator 만 가지고 있어서 인덱스 기반 접근이 불가능
- 시퀀스 연산에는 데코레이터 적용 및 이터레이터 호출의 오버헤드가 있어서 짧은 배열은 시퀀스 안쓰는게 나을 수 있음

---

(김승수)
### Q1) 빈 리스트(emptyList)에 .all { ... }를 수행하면 결과는 무엇일까요?

**A) 김규**
- true
- '모든 원소에 대해 참이다' = '거짓인 원소가 하나도 없다' 이므로 빈 배열에 대해 참
- 비슷한 예시
  - `any`: '해당하는 원소가 하나라도 있다'라서 애초에 원소가 없는 빈 컬렉션에 대해서 false
  - `none`: '해당하는 원소가 하나도 없다'라서 애초에 원소가 없는 빈 컬렉션에 대해서 true

---
    
### Q2) zip함수를 사용할 떄 두 컬렉션의 길이가 다르면 어떻게 동작하나요?

**A) 김세진**

- 더 짧은 쪽의 길이에 맞춰지며, 남는 요소는 버려집니다.
- `zip`은 두 컬렉션의 인덱스를 맞추어 쌍(`Pair`)을 만들다가, 어느 한 쪽이라도 끝나면 즉시 종료됩니다.

```kotlin
val names = listOf("A", "B", "C", "D")
val ages = listOf(20, 30)

val paired = names.zip(ages)
println(paired) // [(A, 20), (B, 30)] -> "C", "D"는 짝을 못 찾아서 버림
```


