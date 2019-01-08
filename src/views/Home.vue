<template>
  <div class="home">
    <ContentLoop :content="content.components" :components="componentDefs" />
  </div>
</template>

<script>
// @ is an alias to /src
import ContentLoop from '@jdplc/jd-components/sfc/ContentLoop.vue';
import Card from '@/components/Card.vue';
import InteractiveBanner from '@/components/InteractiveBanner.vue';
import Timeline from '@/components/Timeline.vue';

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
      InteractiveBanner,
      Timeline,
    },
  }),
};
</script>
