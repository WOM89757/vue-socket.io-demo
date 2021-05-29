<template>
  <div id="app">
    <div id="nav">
      <button @click="connect">连接socket</button>
      <button @click="sendMessage">发送数据</button>
    </div>
  </div>
</template>


<script>
export default {
  name: "Music",
  // conference: {},
  data() {
    
    return {
      conference: {}
     
    }
  },

  mounted() {
    this.connect();
  },

  methods:{

    // 连接socket
    connect() {

      // this.$socket.open()
      // console.log(this.sockets)
      /* 
        vue-socket.io version 3.0.9    
        TypeError: this.sockets.subscribe is not a function

        vue-socket.io version 3.0.7    
          welcome data  欢迎连接socket
      */
     
      // this.sockets.subscribe('welcome', data => {
      //   console.log('welcome data ', data)
      // }) 

      var config = {"rtcConfiguration": {
          "iceServers": [{
                "urls": "stun:139.9.118.13:3478"
      }]}}
      this.conference = new Owt.Conference.ConferenceClient();
      console.log(this.conference);

      //  createToken(myRoom, 'user', 'presenter', function(response) {
       
      //  }

      this.conference.join("eyJ0b2tlbklkIjoiNjBiMjUyYjFiZTcwZDkwMmJmODJhMTRmIiwiaG9zdCI6Im10Z2wuemh1b3l1YW4tdGVjaC5jb206ODA4OSIsInNlY3VyZSI6dHJ1ZSwic2lnbmF0dXJlIjoiWlRrd05ETmtNRGxsTmpSbVpqY3lNR1JtTmpkbVlXRXlZVEV3TkROak1EazBNVEV6TTJOaFlUVm1NV0UxWTJZM05XUXhNalkyWlROa1kyRmtOekV5TWc9PSJ9")
      .then(resp => {
          console.log(resp);
      }, function (err) {
           console.log(err);
      });

      /* 
        vue-socket.io version 3.0.9
        welcome data  欢迎连接socket
      */

      // this.sockets.listener.subscribe('welcome', data => {
      //   console.log('welcome data ', data)
      // })
      
    },

    // 发送消息
    sendMessage() {
      
      /* 
        vue-socket.io version 3.0.9
        socket serve: 接收客户端发送数据 这里是客户端
      */
      this.$socket.emit('hello', '这里是客户端')

    }



  },

  sockets:{

    /* 
      vue-socket.io version 3.0.9
      不能运行
    */
    welcome: data => {
      console.log('welcome data ', data)
    }

  }
}
</script>
