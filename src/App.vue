<template>
  <div class="menu">
    <a href="#" v-for="(item, idx) in menu" :key="idx">{{ item }}</a>
  </div>
  <div>
    <div>
      {{ item }}
      <p>{{ price1 }}만원</p>
      <button @click="increase">허위 매물 신고</button>
      <span> 신고수 :{{ count.first }}</span>
    </div>
    <div>
      {{ item }}
      <p>{{ price1 }}만원</p>
      <button @click="increase2">허위 매물 신고</button>
      <span> 신고수 :{{ count.second }}</span>
    </div>
    <div>
      {{ item }}
      <p>{{ price1 }}만원</p>
      <button @click="increase3">허위 매물 신고</button>
      <span> 신고수 :{{ count.third }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: { first: 0, second: 0, third: 0 },
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      menu: ['Home', 'Products', 'About'],
    };
  },
  methods: {
    increase() {
      this.count.first++;
    },
    increase2() {
      this.count.second++;
    },
    increase3() {
      this.count.third++;
    },
  },
  components: {},
};
</script>

<style>
.red {
  color: red;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
  text-decoration: none;
}
</style>
