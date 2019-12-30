## src
1. java 개발자가 작성한 JAVA 코드저장 (Controller, DAO, VO, Service, ServiceImpl, util)
2. resources 스프링 파일을 설정을 하기 위한 역할, 리소스 파일을 모아서 관리하는 곳 (mapper, ws 등)
3. webapp 웹에서 사용하는 자원들을 모아서 관리 (jsp, js, css, img, xml설정 파일 등)
## pom.xml
maven(apache maven) 사용할 특정 문서를 명시하면 네트워크를 통하여 라이브러리를 매우 손쉽게 다운받을 수 있다.
 - 장점 
 
 	라이브러리의 관리를 매우 용이하게 해줌
 
 	프로젝트의 작성부터 컴파일, 페트스, 라이프사이클에 포함되는 각 테스트를 지원
 
	war파일 기반의 배포용으로도 자주 사용
	
## log4j (Log for java)
Java 기반의 로깅 유틸리티, Apache에서 만듬
Java의 예외를 처리하기 위해 설계

## target 
Maven 으로 빌드하면 생기는 jar 파일을 저장하는 것
결과물인 jar, war 실서버에 반영할 때는 target에서 배포하게 됨
