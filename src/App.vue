<script>
export default {
  data(){
    return {
      title: "My New Vue Title",
      message:"Welcome to Vue",
      isBlue: true,
      input:{
        firstName: '',
        lastName:'',
        isMember: true,
      },
      users: [
        {
          firstName: 'kawamuro',
          lastName: 'hirokazu',
          isMember: false,
        },
        {
          firstName: 'roronoa',
          lastName: 'zoro',
          isMember: true,
        },
        {
          firstName: 'niko',
          lastName: 'robin',
          isMember: true,
        },
      ],
    }
  },
  methods: {
    addUser() {
      this.users.push(this.input)
      this.input = {
        firstName: '',
        lastName: '',
        isMember: true,
      }   
    },
  },
}
</script>

<template>
  <h1 :title="message" :class="{ blue: isBlue }">{{ title }}</h1>
  <input type="text" v-model="input.firstName"/>
  <input type="text" v-model="input.lastName"/>
  <input type="checkbox" v-model="input.isMember"/>
  <button @click="addUser">ユーザー追加</button>
  <h2>ユーザーのデータ</h2>
  <div v-for="user in users">
    <p>Name: {{ user.firstName + ' ' + user.lastName }}</p>
    <p v-if="user.isMember"> メンバーです</p>
    <p v-else>メンバーではありません</p>
  </div>
</template>

<style>
.blue {
  color: blue;
}
</style>