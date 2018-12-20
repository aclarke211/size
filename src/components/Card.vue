<template>
  <a class="card__container" :href="cardContent.url" v-if="cardContent">
    <ImageModule :images="cardContent.images" />
    <p class="card-title">{{ cardContent.text }}</p>
    <CTAsModule :ctas="cardContent.ctas" />
  </a>
</template>

<script>
import ImageModule from '@/modules/ImageModule.vue';
import CTAsModule from '@/modules/CTAsModule.vue';

export default {
  name: 'Card',
  components: {
    ImageModule,
    CTAsModule,
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
    text-decoration: none;

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
