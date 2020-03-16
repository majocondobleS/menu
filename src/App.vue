<template lang="pug">
  .app
    div.sebas(@click="traer") Traer datos Covid-19 
    div(v-for="caso in covidCases")
      p Casos: {{ caso.cases }}
      p Muertes: {{ caso.deaths }}
      p Salvados: {{ caso.recovered }}
</template>

<script>
const axios = require("axios").default;

export default {
  name: "app",

  data() {
    return {
      msg: "Welcome, gay",
      isName: false,
      covidCases: []
    };
  },

  methods: {
    changeMsg() {
      this.msg = "bye, gay";
      this.isName = true;
    },
    async traer() {
      const response = await axios.get('https://coronavirus-19-api.herokuapp.com/all')
      this.covidCases = [response.data]
      console.log(response)
    }
  }
};
</script>

<style lang="stylus">
.app {
  text-align: center;
}

.sebas
  color #1b5a8f
  display inline-block
  font-size 30px
  text-align center
  background-color #4682b4
  border-radius 50px
  padding 15px

.sebas:hover
  background-color black
  cursor pointer

</style>
