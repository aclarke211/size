<template>
  <div class="card__container">
    <ImageModule />
    <p class="card-title">{{ cardTitle }}</p>
  </div>
</template>

<script>
import ImageModule from '@/modules/ImageModule.vue';

export default {
  name: 'Card',
  data: () => ({
    cardTitle: 'SHOE NAME',
  }),
  components: {
    ImageModule,
  },
};
</script>

<style lang="scss">
  @import '@/static/css/base/_mixins.scss';

  .card__container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0 auto;

    .card-title {
      font-size: 1.25rem;
      padding: 1.25rem 0;
      margin: 0;
      display: flex;
      justify-content: center;
      text-align: center;
    }
  }
</style>
