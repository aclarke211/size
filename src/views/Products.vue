<template>
  <div class="products__container" v-if="this.content[this.$route.params.year]">
    <h1 class="products-page__title">{{ $route.params.year }}</h1>
    <h2 class="products__subtitle">Products</h2>

    <div v-for="(product, key) in products" :key="key">
    <Card
      :image="productMainImages[key]" :text="product.name">
      </Card>
      <div v-for="(variant, key2) in product.variants" :key="key2"
      @click="changeImage(key, key2)"
      >{{variant.hexForIcon}}</div>
    </div>

  </div>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
  name: 'products',
  components: {
    Card,
  },
  data: () => ({
    pageLoaded: false,
    productMainImages: [],
  }),
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
  methods: {
    changeImage(productKey, variantKey) {
      this.productMainImages = this.createNewProductImagesArray(productKey, variantKey);
    },
    createNewProductImagesArray(productKey, variantKey) {
      const tempArray = [];
      this.products.forEach((product, index) => {
        if (productKey === index) {
          tempArray.push(product.variants[variantKey].images.main.src);
        } else {
          tempArray.push(product.variants[0].images.main.src);
        }
      });
      return tempArray;
    },
  },
  updated() {
    if (!this.pageLoaded) {
      this.productMainImages = this.createNewProductImagesArray(0, 0);
      this.pageLoaded = true;
    }
  },
};
</script>
