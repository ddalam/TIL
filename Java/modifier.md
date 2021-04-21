# 제어자(modifier)

- 클래스, 변수, 메서드의 선언부에 함께 사용해 부가적인 의미를 부여
- 하나의 대상에 여러 제어자를 조합하여 사용 가능(단, 접근 제어자는 하나만 사용 가능)
- 제어자들의 순서는 상관없지만 주로 접근 제어자를 제일 왼쪽에 놓는다

<br/>

### 종류
- 접근 제어자
- 그 외 제어자

<br/>

### `final`
사용될 수 있는 곳 - 클래스, 메서드, 멤버변수, 지역변수

**클래스**
- 변경될 수 없는 클래스, 확장될 수 없는 클래스 → 다른 클래스의 조상이 될 수 없다

**메서드**
- 변경될 수 없는 메서드, 오버라이딩을 통해 재정의 될 수 없다

**멤버변수, 지역변수**
- 값을 변경할 수 없는 상수가 된다


<br/>

---

<br/>
출처
- Java의 정석 - 남궁 성