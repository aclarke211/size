<template>
  <div id="app">
    <router-view v-if="content" :content="content"/>
  </div>
</template>

<script>
import getJSON from '@steriley/jd-components/sfc/utils/fetch';

export default {
  data: () => ({
    content: false,
  }),

  mounted() {
    getJSON('content').then((json) => {
      this.content = json;
    });
  },
};

</script>

<style lang="scss">
html {
  font-size: 16px;
  font-family: Arial, Helvetica, sans-serif;
}

body {
  margin: 0;
  padding: 0;
}
</style>
