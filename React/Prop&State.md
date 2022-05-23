# Component
컴포넌트는 개념적으로 javascript와 유사하다. props라는 입력을 받은 뒤, 화면에 표시해줄 return 값을 반환해준다.
컴포넌트를 선언하는 방식에는 <strong>함수형 컴포넌트</strong>와 <strong>클래스형 컴포넌트</strong> 가 있다.
<br>

## Class Component
React.Component 클래스를 상속받는 것으로 기본 형태를 갖춘다.
컴포넌트는 기본적으로 jsx를 반환해야 하는데, 클래스는 return문을 사용할 수 없기에 클래스형 컴포넌트에서는 jsx를 반환하기 위해 render()함수를 사용한다.
리액트의 경우 클래스형 컴포넌트의 render()함수를 자동으로 실행시킨다.
<br>


### JSX란?
HTML 문법을 JavaScript 코드 내부에 쓴 것을 JSX라 한다.(JavaScript eXtension)

<br>


### rendering 이란?
html 요소(element), 또는 React 요소 등의 코드가 눈으로 볼 수 있도록 그려지는 것을 렌더링(rendering)이라고 한다.

<br>

	
## Function Component
함수형 컴포넌트는, props로 받을 객체 인자를 정의하고, JSX를 반환하는 것으로 기본 형태를 갖춘다.
함수형 컴포넌트에서는 return문에서 JSX를 반환할 수 있다.

<br>

## Prop 
컴포넌트를 사용하는 외부자를 위한 데이터<br>
컴포넌트는, 데이터를 가진 하나의 'props' 객체 인자를 받은 후 React 엘리먼트를 반환한다. 이때 props는 속성을 나타내는 데이터다.<br>
props는 읽기 전용이므로 컴포넌트의 내부에서 props를 수정해서는 안 된다. 입력값을 수정하지 않는 함수를 순수 함수라고 호칭하며,<br> 
모든 React 컴포넌트는 자신의 props를 다룰 때, 순수 함수처럼 동작해야한다.<br>
props를 받는 함수형 컴포넌트에 인자를 정의하면, props를 속성으로 가지는 객체 Object가 해당 인자로 전달된다. <br>
컴포넌트 내부에서 사용 시, 객체에 존재하는 값을 가져오듯 점 연산자(.)를 사용하여 원하는 props를 꺼내 쓸 수 있고, 이를 중괄호로 감싸 {인자이름.props이름} 형태로 사용한다.

```
// 객체 인자를 통해 props 받아오기
function Dog(props) {
	return {
		<div>{props.name}</div>
		<div>{props.age}</div>
	}
}
```



## State
컴포넌트를 만드는 내부자를 위한 데이터<br>
state는 컴포넌트 내부의 동적 데이터를 의미한다. props는 부모 컴포넌트가 설정하는 값으로 컴포넌트 자신은 props를 읽기 전용으로만 사용할 수 있다.<br>
state를 사용하는 방식에는 컴포넌트의 종류에 따라 2가지가 있다. <br>
클래스형 컴포넌트에서는 컴포넌트 자체가 state를 지니는 방식으로 사용한다. 함수형 컴포넌트에서는 useState라는 함수, Hook을 통해 사용한다.<br>












