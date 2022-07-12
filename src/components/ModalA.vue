<template>
  <div class="black-bg" v-if="OpenCloseModal">
    <div class="white-bg">
      <img :src="onerooms[roomid].image" style="width: 100%" />
      <h4>{{ onerooms[roomid].title }}</h4>
      <p>{{ onerooms[roomid].content }}</p>
      <input v-model.number="month" />
      <select v-model="month">
        <option>1</option>
        <option>2</option>
        <option>3</option>
      </select>
      <input type="range" min="1" max="10" name="" id="" value="5" />
      <p>{{ month }}개월 선택함 : {{ onerooms[roomid].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalA',
  data() {
    return {
      month: '',
    };
  },

  props: {
    OpenCloseModal: Boolean,
    onerooms: Array,
    roomid: Number,
  },
};
</script>

<style></style>
