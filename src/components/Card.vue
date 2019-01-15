<template>
  <div class="card__container">
    <ImageModule v-if="images" :images="images"/>
    <p class="card-title" v-if="text">{{ text }}</p>
    <CTAsModule v-if="ctas" :ctas="ctas"/>
  </div>
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
    images: Object,
    text: String,
    ctas: Array,
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
  max-width: 1160px;
  transition: opacity .5s;

  &:hover {
    opacity: .7;
  }

  .card-title {
    font-size: 1.25rem;
    padding: 1.25rem 0;
    margin: 0;
    display: flex;
    justify-content: center;
    text-align: center;
    color: black;
  }
}
</style>
