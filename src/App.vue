<template>
  <div id="app">
    <Navigation :user="user" />
    <router-view :user="user" />
  </div>
</template>
<script>
import db from './db.js'
import Navigation from '@/components/Navigation'
export default {
  name: 'App',
  data: function() {
    return {
      user: null
    }
  },
  mounted() {
    db.collection('users')
      .doc('gV7beTpo7Pp6BembK5te')
      .get()
      .then(snapshot => {
        this.user = snapshot.data().name
        this.toothpaste = snapshot.data().toothpaste
      })
  },
  components: {
    Navigation
  }
}
</script>
<style lang="scss">
$primary: #5f2882;
@import 'node_modules/bootstrap/scss/bootstrap';
</style>
