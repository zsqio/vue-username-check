<template lang="html">
  <div class="search">
    Enter Username:
    <input type="text"
    placeholder="Enter UserName" v-model="username"
    @keypress.enter="checkUser">
    <button v-on:click="checkUser">Search</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      username: ''
    }
  },
  methods: {
    checkUser () {
      if (this.username === '') alert('You must enter your name!')
      else {
        // console.log(this.username)
        this.$emit('CheckUser', this.username)
      }
    }
  }
}
</script>

<style lang="css">
</style>
