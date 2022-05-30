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
  
  
  ## Redux 본격 사용
  ### dispach 를 통해 action 보내기
  ```
  import { useDispatch } from "react-redux";
  
  const blabla=(event)=>{
  dispatch({type:"blabla",payload:{name:name,phoneNumber:phoneNumber}}) 
  };
  ```
  dispatch 안에는 type(어떤상태인지 reduce에서 확인한다.)과 payload(보내줄 값) 을 필수적으로 포함한다.
  
  
  ### reducer를 통해 행동지침 확인하기
  ```
  let initialState ={
     contactList:[];  
  };
  
  function reducer(state=initialState,action){}
    switch(action.type){
      case "blabla":
        return{...state,contactList:[...state.comtactList,{name:action.payload,phoneNumber:action.payload.phoneNumber}]}
    default:
      return {...state};
  }
  
  export default reducer;
  ```
  
  
  
  
  
  
  
