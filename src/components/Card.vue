<template>
  <a class="card__container" :href="url">
    <ImageModule />
    <p class="card-title">{{ cardTitle }}</p>
    <CTAModule />
  </a>
</template>

<script>
import ImageModule from '@/modules/ImageModule.vue';
import CTAModule from '@/modules/CTAModule.vue';

export default {
  name: 'Card',
  data: () => ({
    cardTitle: 'SHOE NAME',
  }),
  components: {
    ImageModule,
    CTAModule,
  },
  props: {
    url: {
      type: String,
      default: '#',
    },
  },
};
</script>

<style lang="scss">
  @import '@/static/css/base/_mixins.scss';

  .card__container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 2rem auto;

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
