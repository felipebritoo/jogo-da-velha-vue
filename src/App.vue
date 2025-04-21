<template>
  <div>
    <h1>Jogo da Velha</h1>
    <Board />
  </div>
</template>

<script>
import Board from './components/Board.vue';

export default {
  name: 'App',
  components: {
    Board,
  },
};
</script>

<style>
body {
  background: linear-gradient(135deg, #ff7e5f, #6b48ff);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
}

h1 {
  text-align: center;
  margin: 20px 0;
  color: #333;
  font-size: 36px;
  font-family: 'Poppins', sans-serif;
}
</style>