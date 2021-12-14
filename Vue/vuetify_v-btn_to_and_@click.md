# Veutify v-btn 의 to 와 @click 이 동시에 작동하지 않은 문제

## 0. 문제

- 버튼 클릭 시 mix panel과 gtm 에 커스텀 이벤트를 보내주면서 link를 통해 다른 페이지로 이동시켜주고자 했음

- 기존에 "to='/location'" 을 통해 이동 시켜주고 있어서 추가로 "@click=function()" 속성을 추가해서 작동시켜주고자 했음

    ```ts
    <template>
        <v-btn to="/location" @click="btnClicked"></v-btn>
    </template>

    <script>
        btnClicked(){
            console.log("something");
        }   
    </script>
    ```

- 그러나 이동은 되지만 @click이 실행되지 않음

<br>

## 1. 해결

- 첫번째 시도 :
    ```ts
    <script>
        btnClicked(){
            console.log("something");
            router.push("/location");
        }   
    </script>
    ```
    - router.push로 명시적으로 이동시켜주려 했음

    - 'Redirected when going ... via a navigation guard.' 라는 error 발생

    - router.push로 이동하고 router guard를 통해서 또 이동하려고 해서 그렇다는 얘기도 있음

    - router.push.catch를 이용하면 된다고 함.

- 두번째 시도 : 
    ```ts
    <template>
        <router-link to="/location">
            <v-btn @click="btnClicked"></v-btn>
        </router-link>
    </template>
    ```
    - v-btn 바깥에 router-link 를 이용하여 이동하도록 만들어주니 해결됐음

    - router 버전 문제라는 얘기도 있는데 어쨌든 이렇게 해결 가능