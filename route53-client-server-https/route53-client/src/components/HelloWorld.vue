<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>v1.3</h1>
    <div>
      <button class="btn button-submit" @click="loadUsers">Load Users...</button>
    </div>
    <h1>{{ serverMsg }}</h1>
  </div>
</template>

<script>
import RestService from '@/services/RestService'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Route53: Client (Vue.js) on S3',
      serverMsg: ''
    }
  },
  methods: {
    loadUsers: function () {
      RestService.methods.getUsers().then((response) => {
        this.serverMsg = 'Users: <' + response.body[0].username + ', ' + response.body[1].username + '>'
      }, (response) => {
        this.serverMsg = 'Sorry, server exception!'
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
