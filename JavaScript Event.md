## 이벤트란?

웹페이지에서 마우스를 클릭했을 때, 키를 입력했을 때, 특정 요소에 포커스가 이동되었을 때 어떤 사건을 발생시키는 것.

## 이벤트의 종류
### UI Event
* Event : Description
* load : 웹페이지나 스크립트의 로드가 완료되었을 때
* unload : 웹페이지가 언로드될 때(주로 새로운 페이지를 요청한 경우)
* error : 브라우저가 자바스크립트 오류를 만났거나 요청한 자원이 존재하지 않는경우
* resize : 브라우저 창의 크기를 조절했을 때
* scroll : 사용자가 페이지를 위아래로 스크롤할 때
* select : 텍스트를 선택했을 때

### Mouse Event
* Event : Description
* click : 마우스 버튼을 클릭했을 때
* dbclick : 마우스 버튼을 더블 클릭했을 때
* mousedown : 마우스 버튼을 누르고 있을 때
* mouseup : 누르고 있던 마우스 버튼을 뗄 때
* mousemove : 마우스를 움직일 때(터치 스크린에서 동작하지 않는다.)
* mouseover : 마우스를 요소 위로 움직였을 때 (터치x)
* mouseout : 마우스를 요소 밖으로 움직였을 때(터치 x)
* mouserenter : 해당요소에 마우스 커서를 올려다 놓았을 때
* mouseleave : 해당 요소에 마우스 커서를 빼낼 때


### Keyboard Event
* Event : Description
* keydown : 키를 누르고 있을 때
* keyup : 누르고있던 키를 뗄 때
* keypress : 키를 누르고 뗏을 때
* keyCode : 키 코드값

### Focus Event
* Event : Description
* focus/focusin : 요소가 포커스를 얻었을 때
* blur/foucusout : 요소가 포커스를 잃었을 때


### Form Event
* Event : Description
* input : input 또는 textarea 요소의 값이 변경되었을 때
* change : select box, checkbox, radio button의 상태가 변경되었을 때
* submit : form을 submit할 때(버튼 또는 키)
* reset : reset 버튼을 클릭할 때


### Clipboard Event
* Event : Description
* cut : 콘텐츠를 잘라내기할 때
* copy : 콘텐츠를 복사할 때
* paste : 콘텐츠를 붙여넣기 할 때

## 이벤트 연결

### 이벤트 핸들러
사용자가 실제 이벤트를 발생시켰을 때 그 이벤트에 대응하여 실행되는 함수를 말한다.
이벤트 핸들러는 앞에 on을 붙여주며 이벤트에 대한 동작을 처리한다.

