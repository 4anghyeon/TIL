# Props
- properties의 준말.
- 우리가 어떠한 값을 컴포넌트에 전달해줘야 할 때, props를 사용한다.

## 기본 사용법
### App.js
``` javascript
function App() {
    return (
        <Title title ="test" /> // Ttitle Component로 title 전달
    )
}
```

### Ttile.js
``` javascript
function Ttile(props) { // props를 전달 받아서
    return <h1>제목은 {props.title}</h1> 
    // props에서 원하는 속성이름을 꺼낸다.
}
```
----
 ## Multi Props
``` javascript
function App() {
    return (
        <Title title ="test" color="red" /> // Ttitle Component로 title 전달
    )
}
```

### Ttile.js
``` javascript
function Ttile(props) { // props를 전달 받아서
    return <h1 style={{color: props.color}}>제목은 {props.title}</h1> 
    // props에서 원하는 속성이름을 꺼낸다.
}
```
----
## Props 분해
- 매번 props를 쓰지 않고 다음처럼 props를 분해하여 사용 할 수 있다.
### Ttile.js
``` javascript
function Ttile({title, color}}) { // props 분해
    return <h1 style={{color: color}}>제목은 {title}</h1> 
}
```
----
## defaultProps
- 컴포넌트에 props를 지정하지 않았을 때 미리 기본값을 설정해놓고 사용 할 수 있다.
 ``` javascript
function Ttile({title, color}}) { // props 분해
    return <h1 style={{color: color}}>제목은 {title}</h1> 
}
Title.defaultProps = {
    color : 'blue'
}
```

## props.children
- 컴포넌트 사에에 넣은 값을 출력하고 싶을때는 다음과 같이한다.
### Wrapper.js
``` javascript
function Wrapper({children}) {
    const style = {
        border: '2px solid black',
        padding: '16px'
    };
    return (
        <div style={style}>
            {children}    
        </div>
    )
}
```
### App.js
``` javascript
function App() {
  const now = new Date();
  const date = now.getDate();
  return (
    <Wrapper>
      <Ttitle date={date}/>
    </Wrapper>
  );
}
```
- 최상위 컴포넌트인 Wrapper 컴포넌트 안에 children인 Ttitle을 넘겨 줘야 Title이 출력이 된다.