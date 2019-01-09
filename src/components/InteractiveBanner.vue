<template>
  <div class="interactive-banner__container">
    <div class="images__container">
      <ImageModule
        v-for="(imageVariableInLoop, index) in images"
        :key="index"
        :images="imageVariableInLoop"
      />
    </div>
    <p class="text" :style="inlineStyles">{{ text.value }}</p>
    <div class="toggle-btn" @click="toggleButton()">{{ button.text }}</div>
  </div>
</template>

<script>
import ImageModule from '@/modules/ImageModule.vue';

export default {
  name: 'InteractiveBanner',
  props: {
    images: Array,
    text: Object,
    button: Object,
  },
  components: {
    ImageModule,
  },
  methods: {
    toggleButton() {
      this.text.isShowing = !this.text.isShowing;
    },
  },
  computed: {
    inlineStyles() {
      const styles = {};

      if (this.text.isShowing === true) {
        styles.maxHeight = '1000px';
        styles.opacity = 1;
      }

      return styles;
    },
  },
};
</script>

<style lang="scss">
@import '@/static/css/base/_mixins.scss';

.interactive-banner__container {
  background: lightskyblue;
  padding: 4rem;
  display: flex;
  flex-direction: column;

  .images__container {
    display: flex;
    justify-content: center;

    .img__container {
        width: 20rem;

      .img__outer {
        padding-top: calc(640 / 640 * 100%);

        @include tablet {
          padding-top: calc(485 / 1160 * 100%);
        }
      }
    }
  }

  .text {
    margin: 1rem 0 0;
    padding: 0;
    transition: all 1.5s;
    height: auto;
    max-height: 0;
    opacity: 0;
    overflow: hidden;
  }

  .toggle-btn {
    margin-top: 1rem;
    border-bottom: 2px solid black;
    align-self: center;
    padding-bottom: .5rem;
    transition: all .5s;
    cursor: pointer;

      @include desktop {
        border-color: transparent;

        &:hover {
          border-color: black;
        }
      }
  }
}
</style>
