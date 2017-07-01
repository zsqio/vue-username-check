<template>
  <div id="app">
    <h1>Username - Checker</h1>
    <Search v-on:CheckUser='CheckUser'></Search>
    <Result :github='github'></Result>
  </div>
</template>

<script>
import Search from '@/components/search.vue'
import Result from '@/components/result.vue'
export default {
  name: 'app',
  data () {
    return {
      github: {
        url: '',
        avatar: '',
        state: ''
      }
    }
  },
  created () {
    this.github.state = 'Search Waiting'
  },
  methods: {
    CheckUser (username) {
      alert(username)
      fetch('https://api.github.com/users/' + username)
        .then(response => response.json())
        .then(data => {
          console.log(data)
          if (data && 'id' in data) {
            this.github.url = data.html_url
            this.github.avatar = data.avatar_url
            this.github.state = 'Not Avaliable'
          } else {
            this.github.state = 'Avaliable'
          }
        }).catch(err => {
          console.log(err + 'fdfdfd')
          this.github.state = 'Avaliable'
        })
    }
  },
  components: {
    Search,
    Result
  }
}
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
