<template>
  <div class="timeline__container">
    <div class="timeline-product__container" v-for="(panel, key) in panels" :key="key"
    @click="changeRouteToShowProductDetails()">
       <TimelineProduct :panelContent="panel.panelContent" />
    </div>
  </div>
</template>

<script>
import TimelineProduct from '@/modules/TimelineProduct.vue';

export default {
  name: 'Card',
  components: {
    TimelineProduct,
  },
  props: {
    hoverText: String,
    panels: Array,
  },
  methods: {
    changeRouteToShowProductDetails() {
      this.$router.push('about');
    },
  },
};
</script>

<style lang="scss">
  .timeline__container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 100%;

    .timeline-product__container {
      // width of each timeline product (can be changed to 0 0 50% for two on a line etc.)
      flex: 0 0 33.33%;
      position: relative;
      display: block;
      cursor: pointer;
    }
  }
</style>
