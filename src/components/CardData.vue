<template>
  <div>
    <img v-bind:src="item.image" alt="" class="item_img" />
    <h1 @click="modalOpen">
      {{ item.title }}
    </h1>
    <p>{{ item.price.toLocaleString() }}원</p>
  </div>
</template>

<script>
export default {
  name: 'CardData',
  props: {
    item: Object,
  },
  methods: {
    modalOpen() {
      this.$emit('openModal', this.item.id);
    },
  },
};
</script>

<style></style>
