<template>
  <div class="modal">
    <div class="modal-inner">
      <h1 v-if="uiState === 'won'">You won</h1>
      <h1 v-if="uiState === 'lost'">You lost</h1>
      <img
        src="../assets/face.svg"
        alt=""
        :class="uiState === 'lost' ? 'reverse' : ''"
      />
      <button @click="resetGame">Let's play again!</button>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  methods: {
    resetGame() {
      this.$store.commit("resetGame");
    }
  },
  computed: {
    ...mapState(["uiState"])
  }
};
</script>

<style scoped>
.modal {
  width: 400px;
}

.modal-inner {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.reverse {
  transform: rotate(180deg);
}

button {
  margin-top: 30px;
}
</style>
