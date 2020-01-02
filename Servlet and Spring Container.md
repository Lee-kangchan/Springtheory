# Servlet Container
+ 개발자가 웹서버와 통신하기 위하여 소켓을 생성하고, 특정 포트에 리스닝하고, 스트림을 생성하는 등의 복잡한 일들을 할 필요가 없게 해준다
+ 컨테이너는 서블릿의 생성부터 소멸까지의 라이프 사이클을 관리
+ 요청이 들어올 때마다 새로운 자바 스레드를 만듬.
+ 대표적인 서블릿 컨테이너는 톰캣이며 was가 java파일을 컴파일을해서 Class를 만들고 메모리에 올려 servlet객체를 만듬

## 동작과정
1. url을 클릭하면 HTTP Request를 통하여 Servlet Container에 보냄
2. Servlet Container는 HttpServletRequest, HttpServletResponse 두 객체를 생성
3. 어느 서블릿에 대한 요청인지 URL 분석을 통하여 찾음
4. GET POST여부에따라 doget dopost가 호출
5. 그에 맞는 메소드가 실행하면 동적 페이지를 생성 하고 HttpServletResponse객체에 응답
6. 응답이 완료되면 HttpServletRequest, HttpServletResponse 두 객체를 소멸

## 생명주기
+init() : 서버가 켜질때 한번만 실행
+Service() : 모든 유저들의 요청들을 받음
+destroy() : 서버가 꺼질때 한번만 실행

# Spring Container (Spring Bean Container)
 + Bean들을 생명주기를 관리하며 어플리케이션을 구성하는 Bean을 관리하기위해 IOC를 사용 Spring 컨테이너 종류에는 
 BeanFactory와 이를 상속한 ApplicationContext 존재하며 이 두개의 컨테이너로 의존성 주입된 빈들을 제어하고 관리 할 수 있다.
 + bean 등록 : 메타데이터를 통해 BeanDefinition을 Map<String, BeanDefinition>에 저장한다.
  + getBean 
    + 처음호출 하면 GenericBeanDefinition을 RootBeanDefinition으로 재 정의후 Map<String, BeanDefinition>에 저장하며
    + 쉽게 설명하면 bean instance를 생성 후 Map<String, Object>에 저장 후 반환
    + 2번 이상은 Map<String, Object>ㅇ에 bean instance 꺼내와 반환
 + BeanFactory
  + 스프링 빈 컨테이너에 접근하기 위한 최상위 인터페이스
 + ListableBeanFactory(BeanFactory에 하위 인터페이스이며, Bean을 Listable하게 보관하는 인터페이스를 말함)
 
 ## 웹어플리케이션 동작원리
 1. 웹 애플리케이션이 실행되면 Tomcat(WAS)에 의해 web.xml loading됨
 2. web.xml에 등록되어 있는 ContextLoaderListener(Java Class)가 생성 
 (ServletContextListener 인터페이스를 구현하고 있으며 ApplicationContext를 생성하는 역할)
 3. 생성된 ContextLoaderListener는 root-context.xml을 loading한다.
 4. root-context.xml에 등록되어 있는 Spring Container가 구동(이 때 개발자가 작성한 비즈니스 로직에 대한 부분과 DAO, VO 객체들이 생성)
 5. 클라이언트로부터 웹 애플리케이션이 요청
 6. DispatcherServlet(Servlet)이 생성 FrontController의 역할을 수행
 (클라이언트로부터 요청 온 메세지를 분석하여 알맞은 PageController에게 전달하고 응답을 받아 요청에 따른 응답을 어떻게 할 지 결정만한다.
 실질적인 작업은 PageController에서 이루이지기 때문이다. 이러한 클래스를 HandlerMapping, ViewResolver클래스)
 7.DispatcherServlet은 servlet-context.xml을 loading 함
 8. 두번째 Spring Container가 구동되며 응답에 맞는 PageController들이 동작. 
 이 때 첫번째 Spring Container가 구동되면서 생성된 DAO, VO, ServiceImpl 클래스들과 협업하여 알맞는 작업을 처리
 
