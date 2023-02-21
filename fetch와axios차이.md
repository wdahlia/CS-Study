# Fetch 와 Axios의 차이

- 모두 promise 기반의 HTTP 클라이언트
- 클라이언트를 이용해 네트워크 요청 하면 이행, 거부 할 수 있는 promise 반환
- `fetch`
    - fetch는 .then() 메서드에서 처리된 promise를 반환
    - 아직 필요한 JSON 데이터의 포맷이 아니기 때문에 응답 객체의 .json() 메서드를 호출
    - 그러면 JSON 형식의 데이터로 이행된 또 다른 promise를 반환
    - 일반적인 fetch 요청은 두 개의 .then() 호출을 가짐
    - JSON.stringify()를 사용하여 객체를 문자열로 변환한 뒤 body에 할당
    - 404 에러나 다른 HTTP 에러 응답을 받았다고 해서 promise를 거부하지 않음
    - 네트워크 장애가 발생한 경우에만 promise를 거부 따라서 .then 절을 사용해서 수동으로 HTTP 에러를 처리
- `axios`
    - 응답 데이터를 기본적으로 JSON 타입으로 사용 가능
    - 응답 데이터는 언제나 data 프로퍼티에서 사용 가능
    - 자동으로 데이터를 문자열로 변환