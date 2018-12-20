<template>
  <div class="home">
    <Card/>
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
};
</script>
