<template>
  <div class="products__container" v-if="this.content[this.$route.params.year]">
    <h1 class="products-page__title">{{ $route.params.year }}</h1>
    <h2 class="products__subtitle">Products</h2>
    <Card
      v-for="(product, key) in products" :key="key"
      :image="product.variants[0].images.main.src" :text="product.name"
    />
  </div>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
  name: 'products',
  components: {
    Card,
  },
  props: {
    content: {
      type: [Object, Array],
      default: () => [],
    },
  },
  computed: {
    products() {
      return this.content[this.$route.params.year].products;
    },
  },
};
</script>
