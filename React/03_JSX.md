# JSX란?
- Javascript를 확장한 문법이다.
- Javascript를 이용하여 Html 표현?!

## 주의 할 점
1. 속성은 항상 쌍따옴표로 감싼다.
   ``` html
   <li className="list-item"></li>
   ```
   - html에서는 class이지만 JSX에서는 className이다.
2. 태그는 항상 닫혀 있어야 한다.
3. 어떤 태그도 self-closing이 가능하다.
    ``` html
    <div></div> => <div/>
    ```  
4. 형제 노드를 작성할 수 없다.
   ``` javascript
   render() {
       reutrn (
           <div></div>
           <div></div>
       )
   }
   ```
   따라서 반드시 div나 Fragement태그로 감싸진 형태여야 한다.

   ``` javascirpt
      render() {
       reutrn (
           <Fragement>
                <div></div>
                <div></div>    
           </Fragement>
       )
   }
   ```

## Javascript 변수 사용법
- 변수를 먼저 Render 안에서 정의하고 리턴에서 변수명에 중괄호로 감싼 형태로 표현한다.
  ``` javascript
  render() {
      const name = 'lee'
      const hello = 'hello'
      reutrn (
        <Fragment>
            <div>{name}</div>
            <div>{hello}</div>
        </Fragment>
      )
  }
  ```

### Class와 Style
- JSX에서 style과 class를 설정하는 법은 html에서와 다르다.
  1. 객체 형태로 작성한다.
  2. -(하이픈) 으로 구분되어 있는 애들은 camelCase로 이름 지어준다.
  
    ``` javascript
    const style = {
        backgroundColor : 'black';
        color: 'aqua';
    }

    return (
        <Fragement>
            <div style={style}>
        </Fragment>
    )
    ```
- class는 class가 아니라 className으로 설정한다.

### 주석
- {/* 내용 */} 의 형태로 작성한다.
- 열리는 태그에서는 다음과 같이도 작성 할 수 있다.
    ``` html
    <div // 배경 div입니다.>
    </div>
    ```