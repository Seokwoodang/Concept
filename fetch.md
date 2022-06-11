## fetch API 방식

이벤트 기반인 XMLHttpRequest과는 달리 fetch API는 Promise 기반으로 구성되어 있어 비동기 처리 프로그래밍 방식에 잘 맞는 형태이다.
그래서 then이나 catch 와 같은 체이닝으로 작성할 수 있다는 장점이 있다.
```
fetch('ajax_intro_data.txt')
    .then( response => response.text() )
    .then( text => { document.getElementById("#t").innerHTML = text; } )
 
/* 'fetch('서버주소')' 는 웹 브라우저에게 '이 서버주소로 요청해줘' 라는 의미이고, 
뒤에 .then이 붙으면 '요청 끝나고나서 이 할일을 해줘!' 라는 것이다. */
```
## fetch 문법 & 사용법
```
fetch("https://jsonplaceholder.typicode.com/posts", option)
   .then(res => res.text())
   .then(text => console.log(text));
```
- fetch 에는 기본적으로 첫 번째 인자에 요청할 url이 들어간다.
- 기본적으로 http 메소드 중 GET으로 동작한다.
- fetch를 통해 ajax를 호출 시 해당 주소에 요청을 보낸 다음, 응답 객체(Promise object Response)를 받는다.
- 그러면 첫 번째 then에서 그 응답을 받게되고, res.text() 메서드로 파싱한 text값을 리턴한다.
- 그러면 그 다음 then에서 리턴받은 text 값을 받고, 원하는 처리를 할 수 있게 된다.


## fetch API - GET Method

GET: 존재하는 자원을 요청
  → 단순히 원격 API에 있는 데이터를 가져올 때 쓰임<br/>
  → fetch함수는 디폴트로 GET 방식으로 작동하고, 옵션 인자가 필요 없음.<br/>
  → 응답(response) 객체는 json() 메서드를 제공하고, 이 메서드를 호출하면 응답(response) 객체로부터 JSON 형태의 데이터를 자바스크립트 객체로 변환하여 얻을 수 있음.<br/>
```
fetch("https://jsonplaceholder.typicode.com/posts/1") // posts의 id 1인 엘리먼트를 가져옴 
  .then((response) => response.json())
  .then((data) => console.log(data))
```

```
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit↵suscipit recusandae consequuntur …strum rerum est autem sunt rem eveniet architecto"
}
```

## fetch API - POST Method

POST: 새로운 자원 생성 요청<br/>
  → 폼 등을 사용해서 데이터를 만들어 낼 때, 보내는 데이터의 양이 많거나, 비밀번호 등 개인정보를 보낼 때 POST 메서드 사용<br/>
  → 새로운 포스트 생성 위해서는 method 옵션을 POST로 지정해주고, headers 옵션으로 JSON 포맷 사용한다고 알려줘야 함. body 옵션에는 요청 데이터를 JSON 포맷으로 넣어줌.<br/>

method – HTTP 메서드<br/>
headers – 요청 헤드가 담긴 객체(제약 사항이 있음)<br/>
body – 보내려는 데이터(요청 본문)로 string이나 FormData, BufferSource, Blob, UrlSearchParams 객체 형태<br/>
```
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST", // POST
  headers: { // 헤더 조작
    "Content-Type": "application/json",
  },
  body: JSON.stringify({ // 자바스크립트 객체를 json화 한다.
    title: "Test",
    body: "I am testing!",
    userId: 1,
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data))
```

## fetch API - PUT Method (전체수정)
PUT: 존재하는 자원 변경 요청<br/>
  → API에서 관리하는 데이터의 수정을 위해 PUT 메서드 사용함.<br/>
  → method 옵션만 PUT으로 설정한다는 점 빼놓고는 POST 방식과 비슷<br/>
  → 아예 전체를 body의 데이터로 교체해버림.<br/>

```
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "Test" // 아예 title 엘리먼트로 전체 데이터를 바꿈. 마치 innerHTML같이.
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data))
```

## fetch API - PATCH Method (부분수정)
PATCH: 존재하는 자원 일부 변경 요청<br/>
  → body의 데이터와 알맞는 일부만을 교체함 .<br/>
```
fetch("https://jsonplaceholder.typicode.com/posts/1", { // posts의 id 1인 엘리먼트를 수정
  method: "PATCH",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "Test" // title만 바꿈. 나머지 요소는 건들지 않음.
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data))
```

## fetch API - DELETE Method
DELETE: 존재하는 자원 삭제 요청<br/>
  → 보낼 데이터가 없기 때문에 headers, body 옵션이 필요없음<br/>
```
fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "DELETE",
})
  .then((response) => response.json())
  .then((data) => console.log(data))
```

## fetch - async / await 문법
fetch의 리턴값 response는 Promise객체 이다.<br/>
당연히 await / async 문법으로 보다 가독성을 높이게 코딩 할 수 있다.<br/>
```
fetch("https://jsonplaceholder.typicode.com/posts", option)
.then(res => res.text())
.then(text => console.log(text));
```
```
(async () => {
  let res = await fetch("https://jsonplaceholder.typicode.com/posts", option);
  let text = await res.text();
  console.log(text);
})() //await은 async함수내에서만 쓸수 있으니, 익명 async 바로 실행함수를 통해 활용합니다.
```
