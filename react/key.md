리액트에서 배열을 렌더링 하기 위해서는 key가 사용된다. 리액트를 배우면서 한 번쯤은 짚고 넘어가야 할 key에 대해서, 사용하는 이유와 올바른 사용법을 이번 글에서 알아보고자 한다.



## key를 사용하는 이유

간단한 이해를 위해서 다음과 같은 배열이 있다고 하자.

```javascript
const array = ['a', 'b', 'c', 'd'];
```

그리고 위 배열을 다음과 같이 렌더링 한다고 가정해보자.

```javascript
array.map(item => <div>{item}</div>);
```

<br />
위와 같은 배열의 b와 c 사이에 z를 삽입하게 된다면, 리렌더링을 하는 경우 b와 c 사이에 새로운 div 태그를 삽입하는 것이 아니라 기존의 c는 z로, d는 c로 바뀐 후 맨 마지막에 d가 새롭게 삽입된다.

이후 a, b, z, c, d에서 a를 제거하게 되면, 기존의 a는 b, b는 c, z는 c, c는 d로 바뀌며 맨 마지막에 있는 d는 제거된다.

key가 없는 경우 위와 같이 모든 부분에 변경이 일어나게 되므로 비효율적이라고 할 수 있다.

<br />
이런 부분을 개선하기 위해서 key를 사용할 수 있다. 다음과 같이 객체에 key로 사용할 수 있는 고유한 값이 있고,

```javascript
[
  {
    id: 0,
    text: 'a',
  },
  {
    id: 1,
    text: 'b',
  },
  {
    id: 2,
    text: 'c',
  },
  {
    id: 3,
    text: 'd',
  },
];
```

다음과 같이 렌더링 된다면

```javascript
array.map(item => <div key={item.id}>{item.text}</div>);
```

배열이 업데이트될 때마다 변경되지 않은 값들은 그대로 두고, 원하는 내용을 삽입하거나 삭제할 수 있다.

## key의 올바른 사용법

리액트에서 key로 이용되는 값은 보통 고유한 값이다. 그리고 특별히 인덱스를 key로 사용하는 것은 지양된다. 배열이 재배열되는 과정에서 컴포넌트의 state와 관련된 문제가 발생할 수 있기 때문이다. 즉 컴포넌트 인스턴스는 key를 기반으로 갱신되고 재사용되는데, 인덱스를 key로 사용하게 될 경우, 항목의 순서가 바뀌었을 때 key 또한 바뀔 수 있기 때문이다. 그 결과 의도하지 않은 방식으로 바뀔 수 있다. 다시 말해서, 리스트 아이템의 형제들 사이에서만 고유한 값을 지니면 된다.

하지만 다음과 같은 경우, key로 인덱스를 사용할 수 있다.

- 리스트와 아이템 고정되어, 다시 계산되거나 수정되지 않는다
- 리스트의 아이템에 id가 없다
- 리스트가 재배치되거나 필터되지 않는다

## 정리하면

리액트에서 배열을 렌더링하는 경우, 의도하지 않는 방식의 결과가 나타나거나 비효율적인 동작을 막기 위해서 키가 사용된다. 키는 리스트나 아이템이 고정되어 변경이 일어나지 않는 경우, 인덱스를 사용할 수 있다.

추가적으로 키로 이용할 수 있는 고유한 값으로 id, [uuid](https://github.com/uuidjs/uuid), [nanoid](https://github.com/ai/nanoid/) 등이 있다.

---

### 참고 자료

- [React Document - 리스트와 Key](https://ko.reactjs.org/docs/lists-and-keys.html)
- [React Document - Key](https://ko.reactjs.org/docs/reconciliation.html#keys)
- [벨로퍼트와 함께하는 모던 리액트 - 배열 렌더링하기](https://react.vlpt.us/basic/11-render-array.html)
- [key로 인덱스를 사용하는 것은 anti-pattern이다](https://robinpokorny.medium.com/index-as-a-key-is-an-anti-pattern-e0349aece318)
