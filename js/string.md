# String [*](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)

`String` 전역 객체는 문자열(문자의 나열)의 생성자이다.



## 메서드

- #### `String.fromCharCode()` [*](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)

  - 구문

    ```javascript
    String.fromCharCode(num1[, ...[, numN]])
    ```

  - 설명

    - UTF-16 코드 유닛의 시퀀스로부터 문자열을 생성해서 반환.
    - `String` 객체가 아닌 문자열을 반환.
    - `String`의 정적 메서드이므로 `String.fromCharCode()`로 사용.

  - 매개 변수

    - UTF-16 코드 유닛인 숫자 뭉치. 가능한 값의 범위는 0부터 65535(0xFFFF). 초과하는 값은 짤림.

  - 반환 값

    - 주어진 UTF-16 코드 유닛 N개로 이루어진 문자열.

  - 예시

    ```javascript
    console.log(String.fromCharCode(65)); // "A"
    
    console.log(String.fromCharCode(65, 66, 67, 68)); // "ABCD"
    
    console.log(String.fromCharCode('65')); // "A"
    ```

