// src/router/index.ts (or .js)
import { createRouter, createWebHistory } from 'vue-router'
import Home from '@/components/Home.vue'   // <-- changed path

export default createRouter({
  history: createWebHistory(),
  routes: [
    { path: '/', component: Home },
    // other routes...
  ],
})

