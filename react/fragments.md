# Fragments [*](https://ko.reactjs.org/docs/fragments.html)

- DOM에 별도의 노드를 추가하지 않고 여러 자식을 그룹화하는 방법

- 사용법

  ```react
  // 만들고자 하는 HTML
  <table>
    <tr>
      <td>Hello</td>
      <td>World</td>
    </tr>
  </table>
  
  // 사용법
  class Table extends React.Component {
    render() {
      return (
        <table>
          <tr>
            <Columns />
          </tr>
        </table>
      );
    }
  }
  
  class Columns extends React.Component {
    render() {
      return (
        <React.Fragment>
          <td>Hello</td>
          <td>World</td>
        </React.Fragment>
      );
    }
  }
  ```

- 단축 문법

  ```react
  class Columns extends React.Component {
    render() {
      return (
        <>
          <td>Hello</td>
          <td>World</td>
        </>
      );
    }
  }
  ```

- key가 있는 Fragments

  ```react
  function Glossary(props) {
    return (
      <dl>
        {props.items.map(item => (
          // React는 `key`가 없으면 key warning을 발생합니다.
          <React.Fragment key={item.id}>
            <dt>{item.term}</dt>
            <dd>{item.description}</dd>
          </React.Fragment>
        ))}
      </dl>
    );
  }
  ```

  

