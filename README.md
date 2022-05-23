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


### Store - State : vue 인스턴스의 data 역할
* AllUser 의 data 부분을 store.js 의 state 에 넣어준다.
* main.js 파일에 vue를 설정할 때 store를 선택했기 때문에 store가 셋팅 되어 있음.
* import store가 vue 인스턴스를 생성할 때 이 안에서 하나의 값으로 들어가 있음
* AllUser 파일안에서 data를 가져왔으니, allUsers 적힌 것 부분에 <br>
  store 에서 값을 가져 와야하니깐 allUsers => $store.state.allUsers 로 변경한다.
  

### Store - Getters : 각 컴포넌트의 계산된 속성 (computed) 의 공통 속성으로 정의
* $store.getters.allUsersCount 로 사용한다.
* 주의할 점 allUsersCount(state) 매개변수를 state 로 적어줘야 한다.

  
### ...mapGetters, ...mapState
* $store.getters 가 중복으로 너무 길게 쓰여지는 문제가 있다.
* ...mapGetters 를 사용해보자!
* import { mapGetters } from 'vuex' 임폴트 먼저 한다
* computed 속성안에 ...mapGetters(['', '', '' ]) 배열로 String을 써준다.
* 그러고 $state.getters 를 지우고 메서드만 써주면 된다!
* 객체로 받아 올 수도 있음
* 마찬가지로, $store.state 도 줄여쓰기 위해, <br>
  ...mapState(['allUsers'])로 배열로 받아와서 사용할 수 있다.
* 직관적으로 사용 + 가독성 


### Store - mutations : Vuex 의 데이터, 즉 state 값을 변경하는 로직들을 의미
* computed 가 아닌 methods 에 등록
* commit 을 이용하여 state 를 변경
* Mutations 는 동기적 로직을 정의
* mutations 안에 addUsers 가 singUp 파일에서 실행이 될텐데,<br>
  form 안에 작성된 값들을 같이 넘겨 줘야함.
* addUsers(state, payload) 인자값을 넘겨주자
* singUp 파일에서 mapMutations 임폴트해서 methods 안에 ...mapMutations(['addUsers']) 써준다.
* payload는 this.addUsers(userObj) 의 userOb j이다!

### Store - mutations : commit 사용


