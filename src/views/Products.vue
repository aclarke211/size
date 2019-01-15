<template>
  <div class="products__container" v-if="products">
    <!-- <Card :images="" /> -->
    <h1 v-for="(product, key) in products" :key="key">{{ info.text }}</h1>
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
    info: Object,
  },
};
</script>
