# Assertions

## Object Assertions

### 1. `isEqualTo()` : 객체의 참조를 비교
```java
@Test
    void compareObjects() {
        Dog fido = new Dog("Fido", 5.25F);
        Dog fidosClone = new Dog("Fido", 5.25F);

        // isEqualTo()는 객체의 참조를 비교하기 때문에 실패
        assertThat(fido).isEqualTo(fidosClone);
```

<br/>

### 2. `isEqualToComparingFieldByFieldRecursively()` : 객체의 필드를 재귀적으로 비교
```java
@Test
    void compareObjects() {
        Dog fido = new Dog("Fido", 5.25F);
        Dog fidosClone = new Dog("Fido", 5.25F);

        // 객체의 필드를 재귀적으로 비교하기 때문에 성공
        assertThat(fido).isEqualToComparingFieldByFieldRecursively(fidosClone);
    }
```

<br/>

[AbstractObjectAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractObjectAssert.html)

<br/>

## Boolean Assertions

### 1. `isTrue()`, `isFalse()`
```java
@Test
void assertBoolean() {
    // Boolean에 대한 테스트는 isTrue(), isFalse()를 사용할 수 있다
    assertThat("".isEmpty()).isTrue();
}
```

<br/>

## Iterable/Array Assertions
```java
@Test
void assertIterableOrArray() {
    // 요소가 포함되어 있는지
    List<String> list = Arrays.asList("1", "2", "3");
    assertThat(list).contains("1");
    // 여러개의 element가 포함되어 있는지도 가능
    assertThat(list).contains("1", "3");

    // 비어있는지
    assertThat(list).isNotEmpty();

    // 주어진 문자로 시작되는지
    assertThat(list).startsWith("1");

    // 하나의 객체에 둘 이상의 assertion을 연결할 수 있다
    assertThat(list)
            .isNotEmpty()
            .contains("1")
            .doesNotContainNull()
            .containsSequence("2", "3"); // 실제 그룹이 시퀀스 값 사이에 추가 값없이 순서대로 지정된 시퀀스를 포함하는지 확인
}
```
<br/>

[AbstractIterableAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractIterableAssert.html)

<br/>

## Character Assertions
```java
@Test
void assertCharacter() {
    char someCharacter = 'c';

    // someCharacter가 a가 아니고, 유니코드 테이블에 있는지, b보다 크고, 소문자인지 확인
    assertThat(someCharacter)
            .isNotEqualTo('a')
            .inUnicode()
            .isGreaterThanOrEqualTo('b')
            .isLowerCase();
}
```

<br/>

[AbstractCharacterAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractCharacterAssert.html)

<br/>

## Class Assertions
```java
@Test
void assertClass() {
    // Runnable 클래스가 인터페이스인지 확인
    assertThat(Runnable.class).isInterface();

    // NoSuchElementException 타입을 Exception 타입에 할당 가능한지 확인
    assertThat(Exception.class).isAssignableFrom(NoSuchElementException.class);
}
```

<br/>

## File Assertions
```java
@Test
void assertFile() {
    // 파일이 존재하는지, 디렉토리가 아닌 파일인지, 읽고 쓸 수 있는지 확인
    File someFile = new File("FILE_PATH");
    assertThat(someFile)
            .exists()
            .isFile()
            .canRead()
            .canWrite();
}
```

<br/>

[AbstractFileAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractFileAssert.html)

<br/>

## Numeric Assertions
```java
@Test
void assertNumeric() {
    // withPrecision에 주어진 offset 내의 숫자 값을 비교
    // 주어진 정밀도에 따라 두 값이 같은지 확인
    assertThat(5.1).isEqualTo(5.1, withPrecision(2d));
    assertThat(5.1).isEqualTo(5, withPrecision(1d));
}
```

<br/>

[AbstractDoubleAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractDoubleAssert.html)

<br/>

## InputStream Assertions
```java
@Test
void assertInputStream() {
    // InputSteam의 내용이 주어진 내용과 동일한지 확인
    byte[] actual = new byte[]{1, 2};
    byte[] expected = new byte[]{1, 2};
    ByteArrayInputStream actualInputStream = new ByteArrayInputStream(actual);
    ByteArrayInputStream expectedInputStream = new ByteArrayInputStream(expected);

    assertThat(actualInputStream).hasSameContentAs(expectedInputStream);
}
```

<br/>

[AbstractInputStreamAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractInputStreamAssert.html)

<br/>

## Map Assertions
```java
@Test
void assertMap() {
    Map<Integer, String> map = new HashMap<>();
    map.put(2, "a");
    
    assertThat(map)
            .isNotEmpty()
            .containsKey(2)
            .doesNotContainKeys(10)
            .contains(entry(2, "a"));
}
```

<br/>

[AbstractMapAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractMapAssert.html)

<br/>

## Throwable Assertions
```java
@Test
void assertThrowable() {
    Exception ex = new Exception("abc");

    // 예외가 발생했는지 확인하고, "c"로 끝나는 메시지가 있는지 확인
    assertThat(ex).hasNoCause().hasMessageEndingWith("c");
}
```

<br/>

[AbstractThrowableAssert](https://joel-costigliola.github.io/assertj/core-8/api/org/assertj/core/api/AbstractThrowableAssert.html)

<br/>

## Describing Assertions
```java
@Test
void describeTest() {
    // 테스트에 대한 상세 설명을 위해 as()를 사용할 수 있다
    assertThat(100)
            .as("%s's age should be equal to 100", "Alex")
            .isEqualTo(100);
}
```

<br/>

[AssertJ Core Documentation](https://www.javadoc.io/doc/org.assertj/assertj-core/latest/index.html)

---

<br/>

출처

- [Introduction to AssertJ](https://www.baeldung.com/introduction-to-assertj)