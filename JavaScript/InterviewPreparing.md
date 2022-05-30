## 변수
### 변수란?
어떤 값을 저장하기 위해 확보한 메모리 공간에 붙여주는 호칭을 말한다.



### 변수를 선언한다는 것
```
let score;
```
변수를 생성하는 것을 의미한다. 변수 선언을 통해 메모리 공간을 확보하고 변수의 이름과 확보된 메모리 공간의 주소를 연결해 값을 
저장할 수 있게 준비하는 것이다. 


## let 키워드는 var 키워드와 어떤 점이 다른가요?

#### 1.변수 중복 선언 금지
var 키워드로 이름이 동일한 변수를 중복 선언하면 아무런 에러가 발생하지 않지만<br>
let 키워드로 이름이 같은 변수를 중복 선언하면 문법 에러(SyntaxError)가 발생
```
let bar = 123;
// let이나 const 키워드로 선언된 변수는 같은 스코프 내에서 중복 선언을 허용하지 않는다.
let bar = 456; // SyntaxError: Identifier 'bar' has already been declared
```

#### 2.블록 레벨 스코프
let 키워드를 통해 선언된 변수는 블록 레벨 스코프를 따른다. <br>
함수 뿐만 아니라 모든 코드 블록 내에 선언된 변수(지역 변수)는 해당 유효 범위(스코프)를 벗어나면 사용할 수 없다.
```
let foo = 1; // 전역 변수

{
  let foo = 2; // 지역 변수
  let bar = 3; // 지역 변수
}

console.log(foo); // 1
console.log(bar); // ReferenceError: bar is not defined
```

#### 3.변수 호이스팅
var 키워드로 선언한 변수와 달리 let 키워드로 선언한 변수는 변수 호이스팅이 발생하지 않는 것처럼 동작<br>
런타임 이전에 자바스크립트 엔진에 의해 암묵적으로 선언 단계가 먼저 실행되지만 초기화 단계는 변수 선언문에 도달했을 때 실행
![뀨](https://github.com/junh0328/prepare_frontend_interview/blob/main/images/15_3.jpg)
```
// 런타임 이전에 선언 단계가 실행된다. 아직 변수가 초기화되지 않았다.
// 초기화 이전의 일시적 사각 지대에서는 변수를 참조할 수 없다.
console.log(foo); // ReferenceError: foo is not defined

let foo; // 변수 선언문에서 초기화 단계가 실행된다.
console.log(foo); // undefined

foo = 1; // 할당문에서 할당 단계가 실행된다.
console.log(foo); // 1
```

#### 4. 전역 객체와 let
let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다
```
let x = 1;

// let, const 키워드로 선언한 전역 변수는 전역 객체 window의 프로퍼티가 아니다.
console.log(window.x); // undefined
console.log(x); // 1
```

## const 키워드는 어떤 특징이 있나요?
- const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다. 그렇지 않을 경우 문법 에러(SyntaxError)가 발생한다.
- var 또는 let 키워드로 선언한 변수는 재할당이 자유로우나 const 키워드로 선언한 변수는 재할당이 금지
- const 키워드로 선언한 변수에 원시 값을 할당한 경우 변수 값을 변경할 수 없다. <br>이러한 특징을 이용해 const 키워드를 상수를 표현하는 데 사용하기도 한다.


## TDZ란??
![tdz](https://velog.velcdn.com/images%2Fsoshin_dev%2Fpost%2F53592d46-e4c4-425a-8114-78f64ae040cd%2Fimage.png)
### 변수의 할당 단계
#### 1.선언 단계(Declaration phase)
변수를 실행 컨텍스트의 변수 객체에 등록하는 단계를 의미합니다. 이 변수 객체는 스코프가 참조하는 대상이 됩니다.

#### 2.초기화 단계(Initialization phase)
실행 컨텍스트에 존재 하는 변수 객체에 선언 단계의 변수를 위한 메모리를 만드는 단계 입니다. 이 단계에서 할당된 메모리에는 undefined로 초기화 됩니다.

#### 3.할당 단계(Assignment phase) 
사용자가 undefined로 초기화된 메모리의 다른 값을 할당하는 단계 입니다. 

let, const, class 의 경우 TDZ의 영향을 받지만
var, function,import 의 경우 TDZ의 영향을 받지 않는다.
