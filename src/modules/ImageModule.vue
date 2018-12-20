<template>
  <div class="img__container">
    <picture class="img__outer">
      <source srcset="https://via.placeholder.com/640x800/d9efff/?text=Mobile+(640x800px)"
        media="(max-width: 767px)">
        <img class="img" src="https://via.placeholder.com/1920x800/ffe9b2/?text=Desktop+(1920x800px)" />
    </picture>
  </div>
</template>

<script>
export default {
  name: 'ImageModule',
};
</script>

<style lang="scss">
@import '@/static/css/base/_mixins.scss';

.img__container {
  height: 0;
  padding-top: calc(800 / 640 * 100%);
  position: relative;
  overflow: hidden;
  background: gainsboro;

  @include tablet {
    padding-top: calc(800 / 1920 * 100%);
  }

  .img__outer {
    .img {
      display: block;
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
    }
  }
}

</style>
