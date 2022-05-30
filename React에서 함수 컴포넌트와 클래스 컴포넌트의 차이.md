## 클래스 컴포넌트의 경우
- class키워드로 시작합니다.<br>

![constructor](https://velog.velcdn.com/images%2Fseong-dodo%2Fpost%2Fb8ba8634-7036-4212-a817-8ec05371c325%2Fimage.png)
- 객체지향 프로그래밍의 구조를 띄고 있으며, state를 초기화하기 위해서는 constructor (생성자) 함수를 필요로 합니다.<br>
- 생성자 함수를 통해 state를 초기화해야 하기 때문에 함수 컴포넌트에 비해서 코드가 길어지고, 사이즈가 커질 수 있습니다.<br>
```
constructor(props) {
  super(props);
}
```
- state 기능 및 라이프 사이클 기능을 사용할 수 있으며 임의 메서드를 정의할 수 있다<br>
- render 함수가 꼭 있어야 하고, 그 안에서 보여 주어야 할 JSX를 반환해야 한다.<br>
  (```render```란 컴포넌트를 렌더링하는 메서드로 컴포넌트를 정의할 때 반드시 작성해야하는 함수)

[참고주소](hhttps://velog.io/@seong-dodo/React-%ED%81%B4%EB%9E%98%EC%8A%A4%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-vs-%ED%95%A8%EC%88%98%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8)

## 함수 컴포넌트의 경우 

- Hooks 를 사용하여 생성자 함수를 통해 state를 초기화하지 않더라도 사용이 가능하다 (useState() 등)<br>
- 선언하기가 좀 더 편하고 메모리 자원을 덜 사용한다는 장점이 있다<br>
- 프로젝트를 완성하여 빌드한 후 배포할 때도 함수 컴포넌트를 사용하는 것이 결과물의 파일 크기가 더 작습니다<br>
