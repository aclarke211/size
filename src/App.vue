<template>
  <div id="app">
    <ContentEditor
      v-if="renderEditor"
      :content="content"
      :filename="$route.name"
    />

    <router-view
      v-else
      :content="content"
    />
  </div>
</template>

<script>
import getJSON from '@jdplc/jd-components/sfc/utils/fetch';

export default {
  components: {
    ContentEditor: () => import(/* webpackChunkName: "editor" */ '@jdplc/json-editor'),
  },

  data: () => ({
    content: [],
  }),

  watch: {
    '$route.name': function loadContent() {
      const preview = JSON.parse(localStorage.getItem('json-preview'));

      if (preview !== null && preview.path === this.$route.path) {
        this.content = preview.content;
        return false;
      }

      return getJSON(this.$route.name).then((json) => {
        console.info(json);
        this.content = json;
      });
    },
  },

  computed: {
    renderEditor() {
      return this.$route.query.edit === null;
    },
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
