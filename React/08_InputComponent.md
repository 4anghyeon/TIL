# Input 컴포넌트
- 다음과 같이 값을 선언하고, 바꿔줄 수 있다.
``` javascript
function Input() {

    const [value, setValue] = useState('');

    const onChange = (e) => {
        setValue(e.target.value);
    };

    const onReset = () => {
        setValue('');
    }

    return (
        <div>
            <input onChange={onChange} value={value}/>
            <button onClick={onReset}>초기화</button>
            <div>
                <b>값: {value}</b>
            </div>
        </div>
    )
}
```

## 여러개의 Input 관리하기

``` javascript
function Input() {
    //객체로써 input들의 변수 초기화
    const [inputs, setInputs] = useState({ 
        name: '',
        age: ''
    });

    // 비구조화 할당으로 변수 name과 age에 inputs의 값들을 바로 할당한다.
    const {name, age} = inputs;

    const onChange = (e) => {
        const {value, name} = e.target; // target의 값과 name(속성)값을 가져온다. (<input name="test"/>)
        setInputs({
            ...inputs,
            [name]: value, // 가져온 name의 이름을 가진 객체에 가져온 value를 넣는다.
        })
    };

    const onReset = () => {
        setInputs({
            name: '',
            age: ''
        });
    }

    return (
        <div>
            <input name="name" placeholder="이름" onChange={onChange} value={name}/>
            <input name="age" placeholder="나이" onChange={onChange} value={age}/>
            <button onClick={onReset}>초기화</button>
            <div>
                <h3>이름: {name}</h3>
                <h3>나이: {age}</h3>
            </div>
        </div>
    )
}
```
>**_NOTE_** React에서는 inputs[name]과 같이 직접적으로 값을 수정하면 안되고 ...inputs, [name]: value (전개 구문)와 같이 새로운 객체를 만들어 교체해줌으로써 변화를 감지하게 해줘야 한다. 