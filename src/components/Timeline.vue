<template>
  <div class="timeline__container">
    <div class="timeline-product__container" v-for="(panel, key) in panels" :key="key"
    @click="changeRouteToShowProductDetails(panel)">
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
    changeRouteToShowProductDetails(panel) {
      this.$router.push({ name: 'products', params: { year: panel.panelContent.text } });
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
      // width of each timeline product (0 0 50% for two per row, 0 0 33.33% for three etc.)
      flex: 0 0 20%;
      position: relative;
      display: block;
      cursor: pointer;
    }
  }
</style>
