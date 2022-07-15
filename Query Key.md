queryKey는 React Query에서 중요한 개념이다.<br>
내부적으로 데이터를 캐시하고 쿼리에 대한 종속성이 변경될 때 자동으로 다시 가져올 수 있게 한다. <br>
그리고 필요한 시점에 queryKey를 통해 query cache와 상호작용이 가능하다.<br>

query key는 쿼리에 대해 유니크 한 값을 가져야 하며 react query는 cache에 key를 이용해 접근한다. 
