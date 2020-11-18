<template>
  <div id="app">
    <div class="sidebar bg-dark">
      <div class="header">
<!--        <b-avatar size="lg" class="prof"></b-avatar>-->
        <h3 class="prof" style="color: white">Chat Party</h3>
      </div>
      <Nav />
    </div>
    <div class="main">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Nav from './components/Nav'
// import SockJS from 'sockjs-client/dist/sockjs'
// import Stomp from 'webstomp-client'

export default {
  name: "App",
  components: {
    Nav
  },
  data: ()=>{
    return {
      // uri: 'http://localhost:8080/ws',
      // ws : '',
      // client : null
    }
  },
  methods: {
      // onConnected(frame) {
      //   console.log('connected to server',frame)
      //   this.client.subscribe('/queue/spring',this.onMessage)
      // },
      // onMessage(frame){
      //   console.log(frame.body)
      // }
  },
  mounted() {
    // this.ws = new SockJS(this.uri)
    // this.client = Stomp.over(this.ws)
    // this.client.heartbeat.incoming=10_000
    // this.client.heartbeat.outgoing=10_000
    // this.client.connect({
    //   login : 'guest',
    //   'password': 'guest'
    // },this.onConnected)
  }
}
</script>
<style scoped>
*, body{
  margin: 0;
  padding: 0;
}

#app {
  width: 100%;
  height: 100vh;
  display: flex;
}

.sidebar{
  flex: 0.15;
  /*display: flex;*/
  /*border-right: 1px solid silver;*/
}

.header {
  display: flex;
  height: 100px;
}

.prof {
  margin: auto;
}

.main {
  flex: 1;
  /*background: white;*/
}

@media only screen and (max-width: 900px) {
  .sidebar {
    flex: 0;
    display: none;
  }
}

</style>
