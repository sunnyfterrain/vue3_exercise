<template>
  <div class="menu">
    <a href="#" v-for="item in menu" :key="item.id">{{ item }}</a>
  </div>
  <button @click="priceSort">가격순 정렬</button>
  <button @click="sortBack">되돌리기</button>

  <!-- <div class="start" :class="{ end: OpenCloseModal }"> -->
  <!-- 조건부 클래스 객체형식은 밸류가 트루일때만 넣어줌-->
  <transition name="fade">
    <Modal
      @closeModal="OpenCloseModal = false"
      :OpenCloseModal="OpenCloseModal"
      :onerooms="onerooms"
      :roomid="roomid"
    />
  </transition>
  <!-- </div> -->

  <Discount v-if="showDis" :counts="counts" />
  <div>
    <CardData
      v-for="(item, idx) in onerooms"
      :key="idx"
      :item="item"
      @openModal="
        OpenCloseModal = true;
        roomid = $event;
      "
    />
  </div>

  <div>
    <div v-if="1 === 2">안녕하세요</div>
    <div v-else>어라?</div>
  </div>
</template>

<script>
import discount from '@/components/DiscountView.vue';
import data from '@/assets/data/oneroom';
import Modal from '@/components/ModalA.vue';
import CardData from '@/components/CardData.vue';

export default {
  name: 'App',
  data() {
    return {
      counts: 40,
      showDis: true,
      originOneroom: [...data],
      roomid: 0,
      OpenCloseModal: false,
      onerooms: data,
      count: { first: 0, second: 0, third: 0 },
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      menu: ['Home', 'Products', 'About'],
    };
  },
  mounted() {
    setInterval(() => {
      this.counts--;
    }, 1000);
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
    priceSort() {
      this.onerooms.sort((a, b) => {
        return a.price - b.price;
      });
    },
    sortBack() {
      this.onerooms = [...this.originOneroom];
    },
  },
  components: {
    Discount: discount,
    Modal,
    CardData,
  },
};
</script>

<style>
* {
  margin: 0;
  box-sizing: border-box;
  text-align: center;
}
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

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.item_img {
  width: 100%;
}

.start {
  opacity: 0;
}

.end {
  opacity: 1;
  transition: all 0.5s;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 200ms;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 200ms;
}
.fade-leave-to {
  opacity: 0;
}
</style>
