## Axios 란?
Axios는 브라우저, Node.js를 위한 Promise API를 활용하는 HTTP 비동기 통신 라이브러리 아다.<br/>
쉽게 말해서 백엔드랑 프론트엔드랑 통신을 쉽게하기 위해 Ajax와 더불어 사용한다.<br/>
이미 자바스크립트에는 fetch api가 있지만, 프레임워크에서 ajax를 구현할땐 axios를 쓰는 편이라고 보면 된다.<br/>


## Axios 특징

운영 환경에 따라 브라우저의 XMLHttpRequest 객체 또는 Node.js의 http api 사용<br/>
Promise(ES6) API 사용<br/>
요청과 응답 데이터의 변형<br/>
HTTP 요청 취소<br/>
HTTP 요청과 응답을 JSON 형태로 자동 변경<br/>

## Axios 설치
```
yarn add axios
```

## Axios 문법 구성

axios({
  url: 'https://test/api/cafe/list/today', // 통신할 웹문서
  method: 'get', // 통신할 방식
  data: { // 인자로 보낼 데이터
    foo: 'diary'
  }
});

## axios 요청(request) 파라미터 옵션

method : 요청방식. (get이 디폴트)
url : 서버 주소
baseURL : url을 상대경로로 쓸대 url 맨 앞에 붙는 주소.
          예를들어, url이 /post 이고 baseURL이 https://some-domain.com/api/ 이면,https://some-domain.com/api/post로 요청 가게 된다.
headers : 요청 헤더
data : 요청 방식이 'PUT', 'POST', 'PATCH' 해당하는 경우 body에 보내는 데이터
params : URL 파라미터 ( ?key=value 로 요청하는 url get방식을 객체로 표현한 것)
timeout : 요청 timeout이 발동 되기 전 milliseconds의 시간을 요청. timeout 보다 요청이 길어진다면, 요청은 취소되게 된다.
responseType : 서버가 응답해주는 데이터의 타입 (arraybuffer, documetn, json, text, stream, blob)
responseEncoding : 디코딩 응답에 사용하기 위한 인코딩 (utf-8)
transformRequest : 서버에 전달되기 전에 요청 데이터를 바꿀 수 있다.
                    요청 방식 'PUT', 'POST', 'PATCH', 'DELETE' 에 해당하는 경우에 이용 가능
                    배열의 마지막 함수는 string 또는 Buffer, 또는 ArrayBuffer를 반환합
                    header 객체를 수정 가능
transformResponse : 응답 데이터가 만들어지기 전에 변환 가능
withCredentials : cross-site access-control 요청을 허용 유무. 이를 true로 하면 cross-origin으로 쿠키값을 전달 할 수 있다.
auth : HTTP의 기본 인증에 사용. auth를 통해서 HTTP의 기본 인증이 구성이 가능
maxContentLength: http 응답 내용의 max 사이즈를 지정하도록 하는 옵션
validateStatus : HTTP응답 상태 코드에 대해 promise의 반환 값이 resolve 또는 reject 할지 지정하도록 하는 옵션
maxRedirects : node.js에서 사용되는 리다이렉트 최대치를 지정
httpAgent /  httpsAgent : node.js에서 http나 https를 요청을 할때 사용자 정의 agent를 정의하는 옵션
 proxy : proxy서버의 hostname과 port를 정의하는 옵션
cancelToken : 요청을 취소하는데 사용되어 지는 취소토큰을 명시

```
/* axios 파라미터 문법 예시 */
 
axios({
    method: "get", // 통신 방식
    url: "www.naver.com", // 서버
    headers: {'X-Requested-With': 'XMLHttpRequest'} // 요청 헤더 설정
    params: { api_key: "1234", langualge: "en" }, // ?파라미터를 전달
    responseType: 'json', // default
    
    maxContentLength: 2000, // http 응답 내용의 max 사이즈
    validateStatus: function (status) {
      return status >= 200 && status < 300; // default
    }, // HTTP응답 상태 코드에 대해 promise의 반환 값이 resolve 또는 reject 할지 지정
    proxy: {
      host: '127.0.0.1',
      port: 9000,
      auth: {
        username: 'mikeymike',
        password: 'rapunz3l'
      }
    }, // proxy서버의 hostname과 port를 정의
    maxRedirects: 5, // node.js에서 사용되는 리다이렉트 최대치를 지정
    httpsAgent: new https.Agent({ keepAlive: true }), // node.js에서 https를 요청을 할때 사용자 정의 agent를 정의
})
.then(function (response) {
    // response Action
});
```

## axios 응답(response) 데이터
axios를 통해 요청을 서버에게 보내면, 서버에서 처리를하고 다시 데이터를 클라이언트에 응답 하게 된다.
이를 .then으로 함수인자로(response)로 받아 객체에 담진 데이터가 바로 응답 데이터이다.
 ajax를 통해 서버로부터 받는 응답의 정보는 다음과 같다. 

```
axios({
    method: "get", // 통신 방식
    url: "www.naver.com", // 서버
})
.then(function(response) {
  console.log(response.data)
  console.log(response.status)
  console.log(response.statusText)
  console.log(response.headers)
  console.log(response.config)
})
```
```
{
  data: {}, // 서버가 제공한 응답(데이터)
 
  status: 200, // `status`는 서버 응답의 HTTP 상태 코드
  
  statusText: 'OK',  // `statusText`는 서버 응답으로 부터의 HTTP 상태 메시지
 
  headers: {},  // `headers` 서버가 응답 한 헤더는 모든 헤더 이름이 소문자로 제공
 
  config: {}, // `config`는 요청에 대해 `axios`에 설정된 구성(config)
 
  request: {}
  // `request`는 응답을 생성한 요청
  // 브라우저: XMLHttpRequest 인스턴스
  // Node.js: ClientRequest 인스턴스(리디렉션)
}
```

## Axios 단축 메소드
axios를 편리하게 사용하기 위해 모든 요청 메소드는 aliases가 제공된다.<br/>
위 처럼 객체 옵션을 이것저것 주면 가독성이 떨어지고 너저분하니, 함수형으로 재구성하여 나눠논 것으로 이해하면 된다.<br/>
axios의 Request method에는 대표적으로 다음과 같은 것들이 있다.<br/>

- GET : axios.get(url[, config])
- POST : axios.post(url, data[, config])
- PUT : axios.put(url, data[, config])
- DELETE : axios.delete(url[, config])

```
axios.request(config)
 
axios.get(url[, config])
 
axios.delete(url[, config])
 
axios.head(url[, config])
 
axios.options(url[, config])
 
axios.post(url[, data[, config]])
 
axios.put(url[, data[, config]])
 
axios.patch(url[, data[, config]])

```

### axios GET
1. 단순 데이터(페이지 요청, 지정된 요청) 요청을 수행할 경우
2. 파라미터 데이터를 포함시키는 경우 (사용자 번호에 따른 조회)
```
const axios = require('axios'); // node.js쓸때 모듈 불러오기
 
 
// user에게 할당된 id 값과 함께 요청을 합니다.
axios.get('/user?ID=12345')
  .then(function (response) {
    // 성공했을 때
    console.log(response);
  })
  .catch(function (error) {
    // 에러가 났을 때
    console.log(error);
  })
  .finally(function () {
    // 항상 실행되는 함수
  });
 
 
// 위와는 같지만, 옵션을 주고자 할 때는 이렇게 요청을 합니다.
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  })
  .finally(function () {
    // always executed
  });  
 
 
// async/await 를 쓰고 싶다면 async 함수/메소드를 만듭니다. 
async function getUser() {
  try {
    const response = await axios.get('/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

### axios POST

post 메서드에는 일반적으로 데이터를 Message Body에 포함시켜 보낸다.<br/>
위에서 봤던 get 메서드에서 params를 사용한 경우와 비슷하게 수행된다.<br/>
```
axios.post("url", {
		firstName: 'Fred',
		lastName: 'Flintstone'
    })
    .then(function (response) {
        // response  
    }).catch(function (error) {
        // 오류발생시 실행
    })
```


### axios Delete
delete 메서드에는 일반적으로 body가 비어있다.<br/><br/>
REST 기반 API 프로그램에서 데이터베이스에 저장되어 있는 내용을 삭제하는 목적으로 사용한다.<br/>

```
axios.delete('/user?ID=12345')
  .then(function (response) {
    // handle success
    console.log(response);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
```

```
axios.delete('/user?ID=12345',{
    data: {
      post_id: 1,
      comment_id: 13,
      username: "foo"
    }
  })
  .then(function (response) {
    // handle success
    console.log(response);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
```

### axios PUT
REST 기반 API 프로그램에서 데이터베이스에 저장되어 있는 내용을 갱신(수정)하는 목적으로 사용된다..<br/>
PUT메서드는 서버에 있는 데이터베이스의 내용을 변경하는 것을 주 목적으로 하고 있다.<br/>
put 메서드는 서버 내부적으로 get -> post 과정을 거치기 때문에 post 메서드와 비슷한 형태이다.<br/>
```
axios.put("url", {
        username: "",
        password: ""
    })
    .then(function (response) {
         // response  
    }).catch(function (error) {
        // 오류발생시 실행
    })
```






