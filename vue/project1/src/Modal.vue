<template>
    <Transition name="fade">
    <div class="black-bg" v-if="modal == true">
      <div class="white-bg">
        <h4>{{ rooms[press].title }}</h4>
        <p>{{ rooms[press].content }}</p>
        <!-- <input @input="month = $event.target.value">
         -->
         <input v-model.number="month">
        <p> {{ month }}개월 선택함 : {{ rooms[press].price * month }}원</p>
        <img :src="rooms[press].image" style="width: 100%;">
        <button @click="$emit('closeModal')">닫기</button>
      </div>
    </div>
  </Transition>
</template>

<script>
export default {
    name: 'TheModal',
    data(){
        return {
            month : 1,
        }
    },
    watch : {
        month(a){
            if (isNaN(a)) {
                alert('숫자를 입력하세요.')
                this.month = 1;
            }
        }
    },
    props: {
        rooms : Array,
        press : Number,
        modal : Boolean,
    }
}
</script>

<style>

</style>