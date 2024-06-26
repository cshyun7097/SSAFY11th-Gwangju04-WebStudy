타임리프(Thymeleaf)에서 `th:each`를 사용하여 컬렉션의 요소를 반복 처리할 수 있으며, 이 과정에서 반복 상태 또는 반복 상태 객체를 추적할 수 있습니다. 이 상태 객체는 반복 중인 각 요소에 대한 유용한 정보를 제공합니다, 예를 들어, 현재 반복 카운터, 현재 요소가 첫 번째나 마지막인지 여부, 전체 크기 등이 있습니다.

### 기본 사용법

`th:each` 사용 예시:

```html
<ul>
    <li th:each="item : ${items}" th:text="${item}">Item</li>
</ul>
```

여기서 `${items}`는 반복될 객체(예: 리스트, 세트)입니다. `item`은 현재 반복 중인 요소를 나타냅니다.

### 반복 상태 객체 사용

반복 상태 객체를 사용하여 더 많은 정보를 얻을 수 있습니다. 이 객체는 `iterStat`와 같이 선언하여 사용할 수 있으며, 다음과 같은 정보를 제공합니다:

- `index`: 현재 반복의 인덱스 (0부터 시작)
- `count`: 현재 반복의 카운트 (1부터 시작)
- `size`: 전체 요소의 개수
- `current`: 현재 요소
- `even`, `odd`: 현재 반복이 짝수인지 홀수인지 (boolean 값)
- `first`, `last`: 현재 요소가 첫 번째나 마지막 요소인지 (boolean 값)

#### 예시: 반복 상태 객체 사용

```html
<ul>
    <li th:each="item, iterStat : ${items}" 
        th:text="${iterStat.count} + '. ' + ${item}">
        1. Item
    </li>
</ul>
```

이 예시에서 `item`은 현재 요소를 나타내고, `iterStat`는 반복 상태 객체입니다. `th:text`에서는 `iterStat.count`를 사용하여 각 항목 앞에 순서 번호를 표시합니다.

반복 상태 객체를 사용하면 리스트나 배열을 통해 생성된 UI 요소에서 순서, 짝수/홀수 행 스타일링, 첫 번째나 마지막 요소에 대한 특별한 처리 등을 쉽게 구현할 수 있습니다. 이러한 기능은 테이블 행, 목록 항목, 또는 다른 반복적인 콘텐츠를 동적으로 생성할 때 매우 유용합니다.