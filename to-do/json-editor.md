# Implement JSON Editor

## Notes

- You have to set a unique route path for each router in **router.js**, then set a redirect for the default path *( / )* to one such as */home*.

<br>

## How To

- Install **json-editor** package via NPM:

```js
npm i @jdplc/json-editor
```

- If it has not already been added, also add the **fetch** component:

```js
import getJSON from '@jdplc/jd-components/sfc/utils/fetch';
```

- In **App.vue** add the following in ***export default*** after *imports* in *< script > tag*:

```js
components: {
  ContentEditor: () => import(/* webpackChunkName: "editor" */ '@jdplc/json-editor'),
}
```

- Then add the following also inside the ***export default*** in **App.vue**:

```js
watch: {
  '$route.name': function loadContent() {
    const preview = JSON.parse(localStorage.getItem('json-preview'));

    if (preview !== null && preview.path === this.$route.path) {
      this.content = preview.content;
      return false;
    }

    return getJSON(this.$route.name).then((json) => {
      this.content = json;
    });
  },
},
```

- Also add a new **computed property** inside ***export default*** in **App.vue**:

```js
computed: {
  renderEditor() {
    return this.$route.query.edit === null;
  },
},
```

- Update the **template** in **App.vue** to the following:

```html
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
```


- In **router.js**, create a new ***/home*** route and set it to import a component via a function (inside routes array):

```js
 {
    path: '/home',
    name: 'home',
    component: () => import(/* webpackChunkName: "home" */ './views/Home.vue'),
  },
```

- We can then set the default path to redirect to this new home route:

```js
  {
    path: '/',
    redirect: '/home',
  },
```

- Finally we need to make that the Content File being used by the current route has got the same name as the route does in the **router.js** file.

  - i.e.<br>
    *public/content/uat/gb/home.json*


<br>

## Edit a page

- After implementing the JSON Editor, go to **/?edit** when viewing a page to see the form where content can be edited.

  - i.e.<br>http://localhost:8080/home/?edit
