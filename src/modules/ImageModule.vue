<template>
  <div class="img__container">
    <picture class="img__outer" v-if="images">
      <source :srcset="images.mobile" media="(max-width: 767px)">
      <img class="img" :src="images.desktop" :alt="altText">
    </picture>
    <img v-if="image" class="img" :src="image" :alt="altText">
  </div>
</template>

<script>
export default {
  name: 'ImageModule',
  props: {
    images: Object,
    image: String,
    altText: String,
  },
};
</script>

<style lang="scss">
@import '@/static/css/base/_mixins.scss';

.img__container {
  margin: 0.5rem;
  width: 100%;

  .img__outer {
    height: 0;
    padding-top: calc(800 / 640 * 100%);
    position: relative;
    overflow: hidden;
    background: gainsboro;
    display: block;

    @include tablet {
      padding-top: calc(800 / 1920 * 100%);
    }
    .img {
      display: block;
      width: 100%;
      height: auto;
      position: absolute;
      top: 0;
      left: 0;
    }
  }
}
</style>
