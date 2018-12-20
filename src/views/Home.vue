<template>
  <div class="home">
    <Card :cardContent="cardContent_1"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Card from '@/components/Card.vue';

export default {
  name: 'home',
  components: {
    Card,
  },
  data: () => ({
    cardContent_1: {
      url: '/card-1_URL',
      text: 'TEST TEXT',
      images: {
        mobile: 'https://via.placeholder.com/640x800/d9efff/?text=Mobile+(640x800px)',
        desktop: 'https://via.placeholder.com/1920x800/ffe9b2/?text=Desktop+(1920x800px)',
      },
      ctas: [{
        text: 'New CTA',
        url: '/testCTA',
      },
      {
        text: 'New CTA 2',
        url: '/testCTA+2',
      }],
    },
  }),
};
</script>
