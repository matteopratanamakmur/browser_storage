<template>
  <div class="storage">
    <h2>show cookie</h2>
    <ul>
      <button v-on:click="showCookie">ボタン</button>
      <li v-for="(value, key) in cookies" :key="key">{{ key }} : {{ value }}</li>
    </ul>

    <h2>show localstorage</h2>
    <ul>
      <button v-on:click="showLocalStorage">ボタン</button>
      <li v-for="(value, key) in localStorages" :key="key">{{ key }} : {{ value }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Storage',
  data: function() {
    return {
      cookies: {},
      localStorages: {}
    };
  },
  methods: {
    showCookie: function () {
      var cookies = document.cookie.split(';');
      for(var cookie of cookies){
        var kv = cookie.split('=');
        this.$set(this.cookies, kv[0], kv[1])
      }
    },
    showLocalStorage: function() {
      for( var key in window.localStorage ){
        var value = window.localStorage.getItem(key);
        this.$set(this.localStorages, key, value)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
button {
  color: red;
}
</style>
