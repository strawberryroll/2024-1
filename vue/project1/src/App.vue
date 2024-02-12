<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
      <div>
        <h4 :style="스타일">{{ products[0] }}</h4>
        <p>50 만원</p>
      </div>
      <div>
        <h4 :style="스타일">{{ products[1] }}</h4>
        <p>{{ price }}</p>
      </div>
      <div>
        <h4 :style="스타일">{{ products[2] }}</h4>
        <p>{{ price }}</p>
      </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      price : '가격은아무거나',
      스타일 : 'color:blue',


    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
