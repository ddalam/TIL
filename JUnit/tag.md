# 태깅

`@Tag`를 사용

<br/>

- 테스트를 그룹화하고 원하는 그룹만 테스트를 실행할 수 있다
  ```
  예를 들어,
  로컬에서만 테스트하고 싶은 메서드에는 `@Tag("local")`을 추가하고, CI 빌드 중 실행해야될 테스트 메서드에는 `@Tag("CI")`를 추가한다. 그리고 원하는 태그 그룹만 테스트하도록 필터링을 적용한다
  ```
- 하나의 테스트 메서드에 여러 태그를 사용할 수 있다

<br/>

### 원하는 테스트 그룹만 실행하는 방법

<br/>

---

<br/>

[출처]

- 인프런 더 자바 코드를 테스트하는 다양한 방법 (백기선)