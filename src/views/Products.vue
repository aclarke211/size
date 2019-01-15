<template>
  <div class="products__container" v-if="content">
    <h1 class="products-page__title">{{ $route.params.year }}</h1>
    <!-- <Card :images="" /> -->
    <h2 class="products__subtitle">Products</h2>
    <p v-for="(product, key) in products" :key="key">{{ product.name }}</p>
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
    content: {
      type: [Object, Array],
      default: () => [],
    },
  },
  computed: {
    products() {
      const prods = this.content[this.$route.params.year].products;

      return prods;
    },
  },
};
</script>
