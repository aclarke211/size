<template>
  <div class="ctas__container" v-if="ctas">
    <a class="cta" v-for="(cta, index) in ctas" :key="index" :href="cta.url">
      {{ cta.text }}
    </a>
  </div>
</template>

<script>

export default {
  name: 'CTAsModule',
  props: {
    ctas: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss">
  @import '@/static/css/base/_mixins.scss';

  .ctas__container {
    @include flex;
    flex-wrap: wrap;
    padding: 0 1rem;

    .cta {
      color: black;
      margin: .5rem;
      font-size: 1rem;
      border-bottom: 2px solid black;
      text-decoration: none;
      padding-bottom: .25rem;
      transition: all .5s;

      @include desktop {
        border-color: transparent;

        &:hover {
          border-color: black;
        }
      }
    }
  }
</style>
