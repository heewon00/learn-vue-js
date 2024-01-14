<template>
  <!-- submit 이벤트가 발생하면 submitForm 매서드가 발생함 -->
  <!-- form의 기본적인 action은 새로고침 -> 기본적 동작 막기위해 .prevent 이용 -->
  <form action="" @submit.prevent="submitForm">
    <div>
      <label for="userId">ID:</label>
      <input id="userId" type="text" v-model="username">
    </div>
    <div>
      <label for="password">PW:</label>
      <input type="text" v-model="password">
    </div>
    <button type="submit">로그인</button>
  </form>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue';

  export default {
    // <<composition API>>
    setup() {
      // data
      var username = ref('');
      var password = ref('');

      // methods
      var submitForm = () => {
        axios.post('https://jsonplaceholder.typicode.com/users/', {
          //username, password: 서버로 보낼 속성 이름
          username: username.value,
          password: password.value
        }).then(response => {
          console.log(response);
        })
      }
      
      return { username, password, submitForm }
    },
    // 위에서 return했던 것은 method, template 표현식에서도 동일하게 쓸 수 있음
    // methods: {
    //   logText() {
    //     this.password
    //   }
    // }


    // <<option API>>
    // data() {
    //   return {
    //     username: '',
    //     password: '',
    //   }
    // },
    // methods: {
    //   submitForm() {
    //     // event.preventDefault();
    //     const data = {
    //       username: this.username,
    //       password: this.password,
    //     }
    //     axios.post('https://jsonplaceholder.typicode.com/users/', data)
    //       .then(response => {
    //         console.log(response)
    //       });
    //     // console.log('제출됨')
    //   }
    // }
  }
</script>

<style scoped>

</style>