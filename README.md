# size-vue
## Notes
### Displaying Products (products by year page, after clicking timeline)
#### Use a second JSON file for the products
The **ContentLoop** will try to find a json file to use for a page based of the name of the route.

We could set this file up with an **array** of variants to support the different colours.


### Changing Views
Change routes using Vue's [Dynamic Route Matching](https://router.vuejs.org/guide/essentials/dynamic-matching.html).

In the ***router.js*** file you set a variable in the route path **(:year)**. <sup>(Note the colon before the id name)</sup>

```js
{
      path: '/products/:year',
      name: 'products',
      component: () => import(/* webpackChunkName: "products" */ './views/Products.vue'),
      props: true,
},
```

The above is essentially saying when a user goes to a url such as `/products/2009` then display the ***Products.vue*** file.

We set the following to allow the route to be passed props <sup>(i.e. when we change view by clicking an item in ***Timeline.vue***, we want to pass through the value to be stored in the **year** variable).</sup>
```js
props: true
```

Here in ***Timeline.vue*** we change to the Products view and pass through the **year** variable as a prop.
```js
changeRouteToShowProductDetails(panel) {
      this.$router.push({ name: 'products', params: { year: panel.panelContent.text } });
    },
```


Setting the `:year` variable allows us to access the variable <sup>(i.e. 2009)</sup> in a component/view via:
```js
$route.params.year
```



---------------------------------------
## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Run your unit tests
```
npm run test:unit
```
