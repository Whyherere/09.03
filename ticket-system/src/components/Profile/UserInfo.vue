<template>
    <v-app>
      <v-main>
        <div>
          <div v-if="this.user != ''">
            <img class="img" src="https://sun1-20.userapi.com/s/v1/ig2/QMbUxDekZdcFqMtVg66ieGV15hgouRDJ9GGYfr-h2myeHUEdRl7tmQMZ6MJpMfOpeBVPuNCWsNlCaIPCfx4w7rOX.jpg?size=2400x2400&quality=95&crop=0,0,2400,2400&ava=1">
            <p>Имя: {{ this.user.fullname }}</p>
            <p>Логин: {{ this.user.login }}</p>
            <p>e-mail: {{ this.user.email }}</p>
            <p>роль: {{ this.user.role }}</p>
            <button class="but" @click="logOut">выйти с аккаунта</button>
          </div>
          <p v-else>вы не авторизованы</p>
          <!-- <p>роль: {{ this.user != '' ? '' +this.user.role: 'вы не авторизованы' }}</p> -->
        </div>
        </v-main>
    </v-app>
  </template>
  
  <script>
  
  
  export default {
    name: 'UserInfo',
  
    components: {
      
    },
  
    data: () => ({
      //
    }),
    computed: {
      user(){
        return this.$store.state.user.curUser
      }
    },
    methods: {
      logOut(){
        this.$store.commit('LOGOUT')
        this.$router.push('/login')
      }
    }
  }
  </script>
  
<style>
  .img{
    height: 100px;
    width: 100px;
  }
  .but{
    margin: auto;
    width: 150px;
    border: 1px solid black;
    border-radius: 5%;
  }

</style>