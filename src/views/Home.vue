<template>
  <section class="home-container">
    <article>
        <h4>HomePage</h4>
        <Content/>
    </article>
  </section>
</template>

<script setup>
import Content from '../components/Content.vue';


</script>

<style lang="css" scoped>
    .home-container {
        width: 100%;
    }
    h4 {
        font-size: 2rem;
    }
</style>
