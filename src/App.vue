<template>
  <div class="container">
    <Todos />
  </div>
</template>

<script setup>
import Todos from './components/Todos.vue';

</script>
<style scoped>


.container {
  width: 100vw;
  background: #180A0A;
  max-width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 1rem;
}



</style>
