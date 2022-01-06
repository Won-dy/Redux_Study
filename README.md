# Redux_Study
Redux Study

### Redux Map (redux의 전체적인 흐름)
![ReduxMap](https://user-images.githubusercontent.com/65672148/148309920-9fb3fcbe-9214-4642-afb3-95043d8986f6.png)

은행(정보 저장소) - store / 창구 직원 - dispatch, subscribe, getState

store > state: 모든 실제 정보(글 목록, 선택한 글 id 등) 저장 / 개발자가 state에 직접 접속 절대 불가 > 누군가를 통해서 접근

store > reducer: store를 만들 때 reducer라는 함수를 만들어서 공급

createStore 시 reducer 함수를 인자로 등록

![Redux_createStore](https://user-images.githubusercontent.com/65672148/148312035-0f17a3d2-eb19-44f5-b01d-d76767a0c58e.png)

render: state 값을 참조해서 UI를 만들어주는 역할

getState로 state의 값을 가져오고 innerHTML을 통해 state 값을 이용해 HTML page 작성

![Redux_render](https://user-images.githubusercontent.com/65672148/148310901-19bbf675-23d1-4482-8c4b-9d0d7348031e.png)

render는 내부적으로 store에서 데이터를 가져오고 getState는 state에서 값을 가져와 render에게 값 전달 / 직접 접근 시 state 값을 망가뜨릴 수도 있으므로 금지

render 실행하면 언제나 현재 state 값을 반영한 UI를 만듦

store의 subscribe에 render함수를 등록 -> state값이 바뀔 때마다 render 함수를 호출하여 UI가 새롭게 갱신
![Redux_subscribe](https://user-images.githubusercontent.com/65672148/148311412-ba584dd3-bfd9-4d73-92f5-5e6faf2edf5c.png)

submit의 event

![Redux_dispatch](https://user-images.githubusercontent.com/65672148/148311647-03b9e4b3-45b0-427c-b714-227226be6fd2.png)

store의 dispatch에게 {객체}(action)을 전달

dispatch의 역할
1. reducer를 호출해서 state 값을 변경
2. subscribe를 이용해 render함수 호출 -> 화면 갱신

dispatch가 reducer를 호출할 때 2개의 값 전달 (state: 현재 state 값, action: action 데이터{객체})
reducer의 return 객체는 state의 새로운 값이 됨

![Redux_reducer](https://user-images.githubusercontent.com/65672148/148312923-77eb5dbc-b780-4c6d-9ccf-d564c296d3ed.png)

reducer는 state를 입력값으로 받고, action을 참조해서 새로운 state값을 만들어내서 return해 새로운 state로 변경 (state 가공자)

state가 새로운 값으로 변경되면 dispatch가 subscribe를 모두 호출해 render를 호출

render는 getState를 통해 state값을 가져와서 render가 새로운 state값으로 UI 새로 갱신

### 핵심

1. state
2. state 값을 기반으로 화면에 그려준다.
3. store 내의 state에 직접 접근하는 것이 금지되어 있으므로 getState를 통해 값을 가져오고, dispatch를 통해 값을 변경시키고, subscribe를 이용해 값이 변경됐을 때 구동될 함수들을 등록해준다.
4. reducer를 통해서 state 값을 변경한다.

출처: 생활코딩 Youtube
