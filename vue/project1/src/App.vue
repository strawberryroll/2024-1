<template>

  <Transition name="fade">
    <Modal @closeModal="modal = false;" :rooms="rooms" :press="press" :modal="modal"/>
  </Transition>

  <div class="menu">
    <a v-for="(a,i) in menu" :key="i">{{ a }}</a>
  </div>

  <Discount></Discount>
  <button @click="priceSort()">가격순정렬</button>
  <button @click="priceRSort()">가격역순정렬</button>
  <button @click="charSort()">가나다순정렬</button>
  <button @click="sortBack()">되돌리기</button>


  <Card @openModal="modal = true; press = $event" :room="rooms[i]" v-for="(a,i) in rooms" :key="i" />
  <!-- <Card :room="rooms[1]"/>
  <Card :room="rooms[2]"/>
  <Card :room="rooms[3]"/>
  <Card :room="rooms[4]"/>
  <Card :room="rooms[5]"/> -->

  
  <!-- <div>
      <div v-for="(room,i) in rooms" :key="i">
        <img :src="room.image" class="room-img">
        <h4 @click="modal = true; press = i">{{ room.title }}</h4>
        <p>{{ room.price }}원</p>
      </div>
      //
      <div>
        <img :src="rooms[0].image" class="room-img">
        <h4 @click="modal = true">{{ products[0] }}</h4>
        <h4>{{ rooms[0].title }}</h4>
        <p>{{ rooms[0].price }}원</p>
        <button @click=increase(0)>허위매물신고</button> <span>신고수 : {{ report[0] }}</span>
      </div>
      //
  </div> -->



</template>

<script>

import data from './assets/data';
import TheDiscount from './Discount.vue';
import TheModal from './Modal.vue';
import TheCard from './Card.vue';
// import func from 'vue-editor-bridge';

export default {
  name: 'App',
  data(){
    return {
      originalrooms : [...data],
      press : 0,
      rooms : data,
      modal : false,
      report : [0,0,0],
      menu : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      price : [50, 60, 70],
    }
  },
  methods : {
    increase(i){
      this.report[i]++;
    },
    priceSort(){
      this.rooms.sort(function(a,b){
        return a.price - b.price;
      })
    },
    priceRSort(){
      this.rooms.sort(function(a,b){
        return b.price - a.price;
      })
    },
    charSort(){
      this.rooms.sort(function(a,b){
        return a.title.localeCompare(b.title);
      })
    },
    sortBack(){
      this.rooms = [...this.originalrooms];
    },


  },
  components: {
    Discount: TheDiscount,
    Modal: TheModal,
    Card: TheCard,
  }
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 50%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  margin: 0 auto;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}



</style>
