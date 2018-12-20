<template>
  <div class="ctas__container">
    <a class="cta" v-for="(button, key) in buttons" :key="key" :href="button.url">{{ button.text }}</a>
  </div>
</template>

<script>

export default {
  name: 'CTAModule',
  data: () => ({
    buttons: [{
      text: 'New CTA',
      url: '/testCTA',
    },
    {
      text: 'New CTA 2',
      url: '/testCTA+2',
    }],
  }),
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
