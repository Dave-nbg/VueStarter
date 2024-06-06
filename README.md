# Readme

## Stap 1: voorbereiding
Zorg dat je Node hebt gedownload. [Node](https://nodejs.org/en)

## Stap 2: installeer vue cli
```
npm install -g @vue/cli
```

## Stap 3: maak vue project
let op vue-starter is variabel.
```
vue create vue-starter
```

Als je error krijgt dan doe eerst dit command:
```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

## Stap 4: CD
```
cd vue-starter
```
Let op ook hiet is vue-starter variabel

## Stap 5: npm start
```
npm run serve
```

# Router
## Stap 1: installeer router
doe eerst weer de cd.
Doe vervolgens:
```
vue add router
```

## Controle stap
Als index en app.js niet goed zelf doen doe dit:
#### Index.js
```
import Vue from 'vue';
import VueRouter from 'vue-router';
import Home from '../views/Home.vue';
import About from '../views/About.vue';

Vue.use(VueRouter);

const routes = [
  {
    path: '/',
    name: 'Home',
    component: Home
  },
  {
    path: '/about',
    name: 'About',
    component: About
  }
];

const router = new VueRouter({
  mode: 'history',
  base: process.env.BASE_URL,
  routes
});

export default router;

```

#### App.js
```
<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
nav {
  padding: 1em;
}
nav a {
  margin: 0 1em;
}
</style>
```