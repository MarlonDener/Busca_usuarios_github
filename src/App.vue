<template>
  <div id="app">
    <Header />
      <div id="container">
    <!-- <AreaBusca /> -->
        <router-view></router-view>

      </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
export default {
  components: {Header}

}
</script>

<style>
*{
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
  font-family: 'Nunito', sans-serif;
}
#container{
  width: 100%;
  height: 88vh;
  background-color: #0093E9;
  background-image: linear-gradient(160deg, #0d011d 0%, #060c0b 100%);
  display: flex;
  justify-content: center;
  align-items: center;

}
</style>