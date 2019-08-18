<template>
  <ul>
    <li v-for="(user) in users" :key="user.id">
      {{user.id}}: {{user.name}}
    </li>
  </ul>
</template>

<script>
import axios from 'axios';
export default {
  name: 'app',
  data(){
    return {
      users:[]
    }
  },
  methods: {
    async getUsers(){
      try {
        const res = await axios.get('http://localhost:3000/api/users');
        if(!res) return;
        this.users = res.data;
      } catch (error) {
        // console.log(error);
      }
    }
  },
  mounted(){
    this.getUsers();
  }
}
</script>

<style>

</style>
