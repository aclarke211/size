<template>
  <div class="products__container" v-if="this.content[this.$route.params.year]">
    <h1 class="products-page__title">{{ $route.params.year }}</h1>
    <h2 class="products__subtitle">Products</h2>

    <div v-for="(product, key) in products" :key="key">
      <Card
        :image="productMainImages[key]" :text="product.name">
      </Card>

      <div class="swatches__container">
        <div v-for="(variant, key2) in product.variants" :key="key2"
        @click="changeImage(key, key2)" :style="hexColorStyling(key, key2)" class="swatch"
        >{{variant.hexForIcon}}</div>
      </div>
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
    hexColorStyling(productKey, variantKey) {
      const styles = {};
      styles.backgroundColor = this.products[productKey].variants[variantKey].hexForIcon;
      return styles;
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

<style lang="scss">
@import '@/static/css/base/_mixins.scss';

.swatches__container {
  @include flex;

  .swatch {
    @include flex;
    border-radius: 100%;
    border: 2px solid darkslategrey;
    margin: 1rem;
    width: 4rem;
    height: 4rem;
    font-size: .6rem;
    opacity: .85;
    transition: all .5s;

    &:hover {
      opacity: 1;
    }
  }
}
</style>
