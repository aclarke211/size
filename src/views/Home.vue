<template>
  <div class="home">
    <ContentLoop :content="content.components" :components="componentDefs" />
  </div>
</template>

<script>
// @ is an alias to /src
import ContentLoop from '@steriley/jd-components/sfc/ContentLoop.vue';
import Card from '@/components/Card.vue';

export default {
  name: 'home',
  components: {
    ContentLoop,
  },
  props: {
    content: {
      type: [Object, Array],
      default: () => [],
    },
  },
  data: () => ({
    componentDefs: {
      Card,
    },
  }),
};
</script>
