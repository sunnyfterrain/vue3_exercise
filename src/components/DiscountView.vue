<template>
  <div class="discount">
    <h4>지금 결제하면 {{ counts }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'DiscountView',
  props: {
    counts: Number,
  },
};
</script>

<style>
.discount {
  padding: 20px;
  background: lightblue;
}
</style>
