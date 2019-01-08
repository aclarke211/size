<template>
  <div class="timeline-product" :class="{'color-bg': productContent.colorBG}">
    <ImageModule v-if="productContent.img" :images="imagesForImageModule" />
    <p class="text"> {{ productContent.text }}</p>
  </div>
</template>

<script>
import ImageModule from '@/modules/ImageModule.vue';

export default {
  name: 'TimelineProduct',
  components: {
    ImageModule,
  },
  props: {
    productContent: Object,
  },
  computed: {
    imagesForImageModule() {
      const imgs = {
        mobile: this.productContent.img,
        desktop: this.productContent.img,
      };

      return imgs;
    }
  }
};
</script>

<style lang="scss">
@import '@/static/css/base/_mixins.scss';

  .timeline-product {
    border: 1px solid darkgrey;
    height: 0;
    overflow: hidden;
    position: relative;
    background: gainsboro;
    display: block;
    padding-top: 100%;
    width: 100%;

    &.color-bg {
      background-color: royalblue;
      color: white;
    }

    .img__outer {
      padding-top: 100%;

        @include tablet {
          padding-top: 100%;
        }
    }

    .text {
      margin: 0;
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1;
      font-size: 1.25rem;
    }

    .img__container {
      top: 0;
      left: 0;
      position: absolute;
      margin: 0;
      z-index: 0;
    }
  }
</style>
