<template>
  <div>
    <TheHeader />
    <main class="main-content">
      <Nuxt />
    </main>
  </div>
</template>

<script>
import TheHeader from '../components/TheHeader/TheHeader.vue';

export default {
  components: {
    TheHeader
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  font-family: "Roboto", sans-serif;
}
.main-content{
  margin-top: 4.5rem;
}
</style>
