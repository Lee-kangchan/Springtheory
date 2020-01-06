# REST
### REST (Representational State Transfer) : 분산 네트워크 프로그래밍의 아키텍처 스타일
+비동기 방식인 HTTP(S)로 호출하여 데이터를 가져오거나 서버로 전달하는 방식
+데이터셋으로 JSON 또는 XML 등을 사용하는데 대체로 JSON 이 일반적

# 특성
+ uri는 https://{serviceRoot}/{collection}/{id} 형식이어야한다
+ GET, PUT, DELETE, POST, HEAD, PATCH, OPTIONS를 지원해야한다
+ API 버저닝은 Major.minor로 하고 uri에 버전 정보를 포함시킨다
