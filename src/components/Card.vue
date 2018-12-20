<template>
  <a class="card__container" :href="cardContent.url" v-if="cardContent">
    <ImageModule />
    <p class="card-title">{{ cardContent.text }}</p>
    <CTAModule :ctas="cardContent.ctas" />
  </a>
</template>

<script>
import ImageModule from '@/modules/ImageModule.vue';
import CTAModule from '@/modules/CTAModule.vue';

export default {
  name: 'Card',
  components: {
    ImageModule,
    CTAModule,
  },
  props: {
    cardContent: {
      type: [Object, Array],
      default: () => [],
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
