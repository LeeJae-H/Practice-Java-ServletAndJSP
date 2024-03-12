## (도메인 모델 및 저장소)
    src/main/java/hello/servlet/domain
    	/member/Member.java
    		회원 도메인 모델
    	/member/MemberRepository.java
    		회원 저장소(싱글톤 패턴 적용)

## (객체) 
    src/main/java/hello/servlet/web
    	/frontcontroller/MyView.java
    		뷰 객체
    	/frontcontroller/ModelView.java
    		모델-뷰 객체

## 프론트 컨트롤러 V1
    src/main/java/hello/servlet/web
    	/frontcontroller/v1/ControllerV1.java
    		컨트롤러 인터페이스
    	/frontcontroller/v1/FrontControllerServletV1.java
    		프론트 컨트롤러 V1
    	/frontcontroller/v1/controller/MemberFormControllerV1.java
    		회원 등록 폼 컨트롤러
    	/frontcontroller/v1/controller/MemberSaveControllerV1.java
    		회원 저장 컨트롤러
    	/frontcontroller/v1/controller/MemberListControllerV1.java
    		회원 목록 컨트롤러
<p align="center">    
  <img src="https://github.com/LeeJae-H/practice-java-spring/assets/122717063/4fdb6eca-f79e-438c-9d8a-10e8611daff8" width="390" height="230">
</p>

- 프론트 컨트롤러 서블릿 하나가 클라이언트의 요청을 받고, 요청에 맞는 컨트롤러를 찾아서 호출한다.   
    - 프론트 컨트롤러를 제외한 나머지 컨트롤러는 서블릿을 사용하지 않는다. 또한, 프론트 컨트롤러는 컨트롤러 인터페이스를 통해 로직의 일관성을 가져간다.

=> 공통 처리가 가능해졌다.
<br></br>
## 프론트 컨트롤러 V2
    src/main/java/hello/servlet/web
    	/frontcontroller/v2/ControllerV2.java
    		컨트롤러 인터페이스
    	/frontcontroller/v2/FrontControllerServletV2.java
    		프론트 컨트롤러 V2
    	/frontcontroller/v2/controller/MemberFormControllerV2.java
    		회원 등록 폼 컨트롤러
    	/frontcontroller/v2/controller/MemberSaveControllerV2.java
    		회원 저장 컨트롤러
    	/frontcontroller/v2/controller/MemberListControllerV2.java
    		회원 목록 컨트롤러
<p align="center">    
  <img src="https://github.com/LeeJae-H/practice-java-spring/assets/122717063/0c720bb9-c21c-4aaf-99ef-1b2c4c949de8" width="410" height="260">
</p>

- 컨트롤러에서 JSP로 포워딩하는 코드의 중복을 뷰 객체(MyView)에서 처리한다.
    - 각 컨트롤러는 단순히 뷰 이름을 포함한 MyView 객체를 프론트 컨트롤러에게 반환하고, 프론트 컨트롤러는 반환 받은 MyView 객체의 메서드를 호출하여 JSP로 포워딩한다. 

=> 포워드 코드의 중복을 제거하였다.
<br></br>
## 프론트 컨트롤러 V3
    src/main/java/hello/servlet/web
    	/frontcontroller/v3/ControllerV3.java
    		컨트롤러 인터페이스
    	/frontcontroller/v3/FrontControllerServletV3.java
    		프론트 컨트롤러 V3
    	/frontcontroller/v3/controller/MemberFormControllerV3.java
    		회원 등록 폼 컨트롤러
    	/frontcontroller/v3/controller/MemberSaveControllerV3.java
    		회원 저장 컨트롤러
    	/frontcontroller/v3/controller/MemberListControllerV3.java
    		회원 목록 컨트롤러
<p align="center">    
  <img src="https://github.com/LeeJae-H/practice-java-spring/assets/122717063/3d545b38-553e-4a73-8007-9cedaa9cabac" width="430" height="270">
</p>

- 컨트롤러에서 지정하는 뷰 이름의 중복을 프론트 컨트롤러(viewResolver)에서 처리한다.
    - 각 컨트롤러는 뷰의 논리 이름을 반환하고, 실제 물리 위치의 이름은 프론트 컨트롤러(viewResolver)에서 처리한다.
    
=> 뷰 이름의 중복을 제거하였다.
<br></br>
- 컨트롤러에서 서블릿 기술(HttpServletRequest, HttpServletResponse)을 사용하지 않는다.
    - 프론트 컨트롤러(createParamMap)에서 요청 파라미터를 처리한 후 컨트롤러에게 Map으로 전달하고, 컨트롤러는 뷰 이름과 뷰에 전달할 모델 데이터를 포함한 ModelView 객체를 프론트 컨트롤러에게 반환한다.

=> 서블릿 종속성을 제거하였다.
<br></br>
## 프론트 컨트롤러 V4
    src/main/java/hello/servlet/web
    	/frontcontroller/v4/ControllerV4.java
    		컨트롤러 인터페이스
    	/frontcontroller/v4/FrontControllerServletV4.java
    		프론트 컨트롤러 V4
    	/frontcontroller/v4/controller/MemberFormControllerV4.java
    		회원 등록 폼 컨트롤러
    	/frontcontroller/v4/controller/MemberSaveControllerV4.java
    		회원 저장 컨트롤러
    	/frontcontroller/v4/controller/MemberListControllerV4.java
    		회원 목록 컨트롤러
<p align="center">    
  <img src="https://github.com/LeeJae-H/practice-java-spring/assets/122717063/1bfa3f7c-5845-42c0-b2d6-11324629cf3a" width="430" height="270">
</p>

- 컨트롤러는 단순히 뷰의 논리 이름만 반환한다. 
    -  프론트 컨트롤러는 모델 객체를 생성해서 컨트롤러에게 파라미터로 전달하고, 컨트롤러는 모델 객체에 값을 담고 뷰의 논리 이름만 프론트 컨트롤러에게 반환한다.

=> 개발자가 단순하고 편리하게 개발할 수 있도록 만들었다.
<br></br>
## 프론트 컨트롤러 V5
    src/main/java/hello/servlet/web
    	/frontcontroller/v5/MyHandlerAdapter.java
    		어댑터 인터페이스
    	/frontcontroller/v5/FrontControllerServletV5.java
    		프론트 컨트롤러 V5
    	/frontcontroller/v5/adapter/ControllerV3HandlerAdapter.java
    		ControllerV3 처리 어댑터
    	/frontcontroller/v5/adapter/ControllerV4HandlerAdapter.java
    		ControllerV4 처리 어댑터
<p align="center">    
  <img src="https://github.com/LeeJae-H/practice-java-spring/assets/122717063/c1aa3ade-1b6c-4d92-b4e0-8a8c851b4a5c" width="550" height="300">
</p>

- 어댑터 패턴을 사용해서 프론트 컨트롤러가 다양한 방식의 컨트롤러를 처리한다.
    - 프론트 컨트롤러(getHandlerAdapter)는 컨트롤러(핸들러)를 처리할 수 있는 어댑터를 찾고, 어댑터를 통해서 컨트롤러(핸들러)를 호출한다. 또한, 프론트 컨트롤러는 어댑터 인터페이스를 통해 로직의 일관성을 가져간다.

=> 개발자가 유연하고 확장성 있게 개발할 수 있도록 만들었다.
