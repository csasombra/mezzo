<template>
  <div id="app">
    <Home/>
  </div>
</template>

<script>
import Home from 'src/components/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>
<style lang="scss">
@import "~assets/style/colors.scss";

.text-primary{
  color: $primary !important;
}

.text-warning{
  color: $warning !important;
}
.btn-primary{
 background: $primary !important;
 border: solid 1px $primary !important;
}

.btn-warning{
  border: solid 1px $warning !important;
  background: $warning !important;
  color: white !important;
}

.btn{
  border-radius: 1px !important;
  height: $height !important;
}

.form-control{
  border-radius: 1px !important;
  border: 0px !important;
  height: $height !important;
}

.mx-datepicker{
  float: left !important;
  width: 14% !important;
  margin-left: 1% !important;
}

.mx-input-wrapper, .mx-input-wrapper input{
  height: $height !important;
  margin-top: 1vh !important;
  margin-bottom: 1vh !important;
  width: 100% !important;
  float: left !important;
  border: 0px !important;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

ul{
  margin: 0;
  padding: 0;
  list-style: none;
}

@media screen and (max-width: 992px){
  .mx-datepicker{
    width: 48% !important;
  }
}
</style>
