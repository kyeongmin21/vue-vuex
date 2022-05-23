# vuex-project

### Vuex
* vue.js 애플리케이션에 대한 상태 관리 패턴 + 라이브러리
* 중앙 집중식 저장소 역할
* 예측 가능한 방식으로 상태를 변경할 수 있다.


### Project setup
* Users 안에 AllUsers, SignUp 자식 컴포넌트들이 있다.
* AllUsers : data안에 모든 유저들의 정보가 저장되어 있고, <br>
  EventBus 가 signUp 시그널을 듣고, 시그널이 오면 users 에 담아서 allUsers 로 보냄
* SignUp : form 에서 v-model 로 바인딩 되어 있고,<br>
  signUp 버튼 클릭하면 userObj 객체를 이벤트 버스로 보냄, 초깃값 메서드도 만들어 준다.
* EventBus > main.js 에 설정

### 
