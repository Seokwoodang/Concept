# WebRTC

## 1. SDP 교환 - Offer, Answer

![webrtc-signaling-servers](https://doublems.github.io/assets/postphoto/20210720/img_1.png)

1~4 는 Offer-Answer 에 관한 내용이고 SDP를 생성하여 시그널링을 수행하는 과정이다.

![signalling](https://doublems.github.io/assets/postphoto/20210720/img_3.png)

Alice와 Bob 두명의 Peer가 있다. Alice와 Bob은 서로 SDP 기반의 Offer와 Answer 메시지를 주고 받는다.   

1. Alice 가 SDP 형태의 Offer 메시지를 생성한다.
2. Alice가 생성된 Offer 메시지를 본인의 LocalDescription으로 등록한다.
3. Alice가 Offer메시지를 시그널링 서버에게 전달한다.
4. 시그널링서버는 상대방 Bob을 찾아서 SDP 정보를 전달한다.
5. Bob은 전달받은 Offer메시지를 본인의 RemoteDecsription에 등록한다.
6. Bob은 Answer 메시지를 생성한다.
7. 생성된 Answer 메시지를 본인의 LocalDescription으로 등록한다.
8. Bob은 Answer 메시지를 시그널링서버에게 전달한다.
9. 시그널링서버는 상대방 Alice를 찾아서 Answer 메시지를 전달한다.
10. Alice는 전달받은 Anser 메시지를 본인의 RemoteDescription에 등록한다.

## 2. ICE 협상 (ICE Negotiation)
SDP를 서로 교환한 후, 각 Peer Alice와 Bob 은 서로의 주소 값을 알기 위해 ICE Candidate(ICE 후보)를 교환한다.   
이때 사용되는 기술이 NAT Traversal 이다.



















## RTCDataChannel (en-US)
연결된 두 피어간의 양방향 데이터 채널을 나타낸다

## RTCPeerConnection 
로컬 컴퓨터와 원격 피어 간의 WebRTC 연결을 담당하며 원격 피어에 연결하기 위한 메서드들을 제공하고,    
연결을 유지하고 연결 상태를 모니터링하며 더 이상 연결이 필요하지 않을 경우 연결을 종료합니다.   


## RTCDataChannelEvent
RTCDataChannel (en-US)을 RTCPeerConnection에 연결하는 동안 발생하는 이벤트를 나타낸다.
이 인터페이스와 함께 전송되는 유일한 이벤트는 datachannel이다.

https://doublem.org/webrtc-story-02/
