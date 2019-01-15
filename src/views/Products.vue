<template>
  <div class="products__container">
    <!-- <Card :images="" /> -->
  </div>
</template>

<script>
// import Card from '@/components/Card.vue';

export default {
  name: 'products',
  // components: {
  //   Card,
  // },
  props: {
    products: {
      type: [Object, Array],
      default: () => [],
    },
  },
};
</script>
