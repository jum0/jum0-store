# DOM / BOM

- Window 객체 아래에 같은 레벨로 document 객체와 EventTarget 생성자, Node 생성자, Document 생성자가 있다. Node 생성자는 EventTarget 생성자를 상속받고, Document 생성자는 Node 생성자를 상속받는다. 여기서 Document 생성자는 document 객체를 만드는데 사용된다. 

  > [인터페이스와 생성자 차이](https://www.javaer101.com/en/article/103444813.html)
  >
  > [생성자의 타입은 function - Answer 답글](https://stackoverflow.com/questions/23052135/what-is-the-difference-between-document-and-document/23052164)

참고로 `window.Document`의 타입이 function으로 나오는 이유는 생성자의 타입은 보통 function이기 때문에.



## DOM

- HTML 문서의 계층적 구조와 정보를 표현하며 이를 제어할 수 있는 API, 즉 프로퍼티와 메서드를 제공하는 트리 자료구조이다.
- 브라우저의 렌더링 엔진은 HTML 문서를 파싱하여 브라우저가 이해할 수 있는 자료구조인 DOM을 생성. 즉, DOM은 HTML 문서를 파싱한 결과물이다.
- 노드 객체들로 구성된 트리 자료구조로, 노드 객체의 트리로 구조화되어 있기 때문에 DOM 트리라고 부르기도 한다.

- document node(문서 노드)는 DOM 트리의 최상위에 존재하는 루토 노드로써 document 객체(window의 document 프로퍼티에 바인딩되어 있다)를 가리킨다.

<img src="images/dom-tree.png" width="50%" alt="dom tree">

<img src="images/inheritance-structure-of-node-object.png" width="50%" alt="inheritance-structure-of-node-object">

## 리플로우와 리페인트의 차이

- 자바스크립트 코드에서 DOM이나 CSSOM을 변경하는 DOM API가 사용된 경우 DOM이나 CSSOM이 변경되는데, 변경된 DOM과 CSSOM은 다시 렌더 트리로 결합되고 변경된 렌더 트리를 기반으로 레이아웃과 페인트 과정을 거쳐 브라우저의 화면에 다시 렌더링한다. 여기서 리플로우는 다시 레이아웃을 계산하는 과정을 말하며, 노드의 추가/삭제, 요소의 크기/위치 변경, 윈도우 리사이징 등 레이아웃에 영향을 주는 변경이 발생한 경우에만 실행된다. 리페인트란 재결합된 렌더 트리를 기반으로 다시 그리는 것을 말한다. 여기서 특징은, 리플로우와 리페인트가 반드시 함께 실행되는 것은 아니라는 것이다. 레이아웃에 영향이 없는 변경은 리플로우 없이 리페인트만 실행된다.