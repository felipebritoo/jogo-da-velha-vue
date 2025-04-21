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
  background: linear-gradient(135deg, #74ebd5, #acb6e5);
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