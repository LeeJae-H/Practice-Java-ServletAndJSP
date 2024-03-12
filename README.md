## 발전 과정 : ServletAndJSP branch -> FrontController branch

### ServletAndJSP branch
	1. Servlet만 사용한 웹 애플리케이션 만들기
 	2. JSP만 사용한 웹 애플리케이션 만들기
  	3. Servlet과 JSP를 사용한 웹 애플리케이션 만들기
   
### FrontController branch
	- Front Controller 패턴을 도입한 MVC 프레임워크 만들기
<br></br>

---
### (도메인 모델 및 저장소)
	src/main/java/hello/servlet/domain
		/member/Member.java
			회원 도메인 모델
		/member/MemberRepository.java
			회원 저장소(싱글톤 패턴 적용)

### 1. 서블릿만 사용
	src/main/java/hello/servlet/web
		/servlet/MemberFormServlet.java
			회원 등록 폼
		/servlet/MemberSaveServlet.java
			회원 저장
		/servlet/MemberListServlet.java
			회원 목록

### 2. JSP만 사용
	src/main/webapp/jsp
		/members/new-form.jsp
			회원 등록 폼 JSP
		/members/save.jsp
			회원 저장 JSP
		/members.jsp
			회원 목록 JSP

#### ->  1, 2 방법의 한계
	- 하나의 서블릿이나 JSP만으로 비즈니스 로직과 뷰 렌더링을 처리하게 되어 유지보수가 어려워진다. 
 	- 또한, 서블릿만 사용하는 경우에는 HTML을 만드는 작업이 복잡하다. 

#### ->  1, 2 방법의 대안 : 서블릿과 JSP를 사용한 간단한 MVC 패턴
	- 비즈니스 로직과 뷰 렌더링의 영역을 나눈다.
		- 컨트롤러(서블릿) : 비즈니스 로직을 실행한다.
		- 모델 : 뷰에 출력할 데이터를 담아둔다.
		- 뷰(JSP) : 모델에 담겨있는 데이터를 사용해 HTML을 생성한다.

### 3. 서블릿과 JSP를 사용한 간단한 MVC 패턴
	src/main/java/hello/servlet/web
		/servletmvc/MvcMemberFormServlet.java
			회원 등록 폼 컨트롤러
		/servletmvc/MvcMemberSaveServlet.java
			회원 저장 컨트롤러
		/servletmvc/MvcMemberListServlet.java
			회원 목록 조회 컨트롤

	src/main/webapp/WEB-INF
		/views/new-form.jsp
			회원 등록 폼 뷰
		/views/save-result.jsp
			회원 저장 뷰
		/views/members.jsp
			회원 목록 조회 뷰

#### ->  3 방법의 한계
	공통 처리의 어려움, 포워드 코드의 중복, 뷰 이름의 중복, 사용하지 않는 코드 등
#### ->  3 방법의 대안 ([FrontController](https://github.com/LeeJae-H/Practice-Java-ServletAndJSP/tree/FrontController))
	컨트롤러 호출 전에 공통 기능을 처리하는 Front Controller 패턴을 도입한다.
 	  
---
###### request, response 학습 
	src/main/java/hello/servlet/basic
	src/main/webapp/basic
