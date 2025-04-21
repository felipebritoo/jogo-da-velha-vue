<template>
  <div class="board">
    <div class="status">{{ status }}</div>
    <div class="board-grid">
      <button
        v-for="(square, index) in squares"
        :key="index"
        :class="['square', { winner: winnerLine && winnerLine.includes(index) }]"
        @click="handleClick(index)"
      >
        {{ square }}
      </button>
    </div>
    <div class="scores">Placar: X - {{ scores.X }} | O - {{ scores.O }}</div>
    <div class="games-played">Partidas jogadas: {{ gamesPlayed }}</div>
    <button class="reset-button" @click="resetGame">Reiniciar Jogo</button>
    <div v-if="gameEnded" class="modal">
      <div class="modal-content">
        <h2>{{ winner ? `Parabéns, ${winner} venceu!` : 'Jogo empatado!' }}</h2>
        <button @click="resetGame">Jogar Novamente</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Board',
  data() {
    return {
      squares: Array(9).fill(null),
      xIsNext: true,
      scores: { X: 0, O: 0 },
      winnerLine: null,
      gameEnded: false,
      gamesPlayed: 0,
    };
  },
  computed: {
    winner() {
      const lines = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8],
        [0, 3, 6], [1, 4, 7], [2, 5, 8],
        [0, 4, 8], [2, 4, 6],
      ];
      for (let i = 0; i < lines.length; i++) {
        const [a, b, c] = lines[i];
        if (
          this.squares[a] &&
          this.squares[a] === this.squares[b] &&
          this.squares[a] === this.squares[c]
        ) {
          return this.squares[a];
        }
      }
      return null;
    },
    status() {
      if (this.winner) {
        return `Vencedor: ${this.winner}`;
      } else if (this.squares.every((square) => square !== null)) {
        return 'Empate!';
      } else {
        return `Próximo jogador: ${this.xIsNext ? 'X' : 'O'}`;
      }
    },
  },
  methods: {
    handleClick(i) {
      if (this.squares[i] || this.gameEnded) return;
      const nextSquares = [...this.squares];
      nextSquares[i] = this.xIsNext ? 'X' : 'O';
      this.squares = nextSquares;
      this.xIsNext = !this.xIsNext;

      const winner = this.winner;
      if (winner) {
        const lines = [
          [0, 1, 2], [3, 4, 5], [6, 7, 8],
          [0, 3, 6], [1, 4, 7], [2, 5, 8],
          [0, 4, 8], [2, 4, 6],
        ];
        const winningLine = lines.find(([a, b, c]) =>
          nextSquares[a] === winner && nextSquares[b] === winner && nextSquares[c] === winner
        );
        this.winnerLine = winningLine;
        this.gameEnded = true;
        this.scores[winner] += 1;
        this.gamesPlayed += 1;
      } else if (nextSquares.every((square) => square !== null)) {
        this.gameEnded = true;
        this.gamesPlayed += 1;
      }
    },
    resetGame() {
      this.squares = Array(9).fill(null);
      this.xIsNext = true;
      this.winnerLine = null;
      this.gameEnded = false;
    },
  },
};
</script>

<style scoped>
.board {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
  background: rgba(255, 255, 255, 0.9);
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.status {
  font-size: 28px;
  font-weight: bold;
  color: #333;
  margin-bottom: 20px;
  text-transform: uppercase;
}

.board-grid {
  display: grid;
  grid-template-columns: repeat(3, 120px);
  gap: 15px;
  justify-content: center;
  align-items: center;
}

.square {
  width: 120px;
  height: 120px;
  background-color: #ffffff;
  border: 3px solid #444;
  border-radius: 10px;
  font-size: 48px;
  font-weight: bold;
  color: #333;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: transform 0.2s, background-color 0.2s;
}

.square:hover {
  background-color: #e6e6e6;
  transform: scale(1.05);
}

.square.winner {
  background-color: #28a745;
  color: white;
  animation: pulse 1s infinite;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.1); }
  100% { transform: scale(1); }
}

.scores {
  margin: 20px 0;
  font-size: 24px;
  font-weight: bold;
  color: #333;
}

.games-played {
  font-size: 20px;
  color: #333;
  margin-bottom: 10px;
}

.reset-button {
  margin-top: 20px;
  padding: 12px 30px;
  font-size: 18px;
  background-color: #ff6b6b;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.reset-button:hover {
  background-color: #e55a5a;
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 30px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.modal-content h2 {
  font-size: 32px;
  color: #333;
  margin-bottom: 20px;
}

.modal-content button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.modal-content button:hover {
  background-color: #0056b3;
}
</style>