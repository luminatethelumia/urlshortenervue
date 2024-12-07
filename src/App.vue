<template>
  <div id="app">
    <nav></nav>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <UrlView :urlList=urlList></UrlView>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import UrlView from './components/UrlView.vue';

export default {
  name: 'App',
  components: {
    UrlView
  },
  data(){
    return {
      apiUrlTest: "https://localhost:8888",
      urlList: []
    }
  },
  methods: {
    async getDataTest() {
            try {
                const res = await fetch(this.apiUrlTest + "/UrlShorten");
                if (!res.ok) {
                  throw new Error(`Response status: ${response.status}`);
                }
                const finalRes = await res.json();
                console.log(finalRes)
                this.urlList = finalRes;
              } catch (error) {
                  console.error(error.message);
                }
        },
  },
  mounted() {
    this.getDataTest()
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

/* #app {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    font-family: Arial, sans-serif;
    background-color: #f4f4f9;
} */

body {
    background-color: grey;
} 

</style>
