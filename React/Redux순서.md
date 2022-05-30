## 기본 Redux 세팅

index.js 에 import { Provider } from "react-redux";
<Provider store={store}> 로 <App/>을 감싸줌  //provider 가 app 을 감싸는 이유는 store 를 제공해주기 위해서 이다.
  
  
  ### store.js를 만들어 주자
  ```
  import {createStore} from "redux";
  
  let store = createStore(reducer);
  ```
  
  reducer가 선언되지 않았으므로
  
  
  
  ### reducer.js를 만들어주자
  ```
  let initialState ={};
  
  function reducer(state=initialState,action){}
  
  export default reducer;
  ```
  
  
  
  ### store.js 수정
  ```
  import {createStore} from "redux";
  import {reducer} from "~~";
  
  let store = createStore(reducer);
  
  export default store;
  ```
  store 를 export 해줌으로서 index.js에서 store 를 사용 가능하도록 해준다.
  
  
  
  
