<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <SolidLoginButton />
    <Upload />
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    'SolidLoginButton': () => import('@/components/solid/SolidLoginButton'),
    'Upload': () => import('@/components/portfolio/Upload'),
  },
}
</script>
