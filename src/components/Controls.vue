<template>
  <div class="control-container">
    <div class="grid">
      <b-button class="btn" @click="clearFn" variant="info">AC</b-button>
      <b-button class="btn" @click="negPosFn" variant="info">±</b-button>
      <b-button class="btn" @click="deleteFn" variant="info">←</b-button>
      <b-button class="btn" @click="divisionFn" variant="info">&div;</b-button>
      <b-button class="btn" @click="insertFn" variant="info">7</b-button>
      <b-button class="btn" @click="insertFn" variant="info">8</b-button>
      <b-button class="btn" @click="insertFn" variant="info">9</b-button>
      <b-button class="btn" @click="multiplyFn" variant="info">x</b-button>
      <b-button class="btn" @click="insertFn" variant="info">4</b-button>
      <b-button class="btn" @click="insertFn" variant="info">5</b-button>
      <b-button class="btn" @click="insertFn" variant="info">6</b-button>
      <b-button class="btn" @click="subtractFn" variant="info">-</b-button>
      <b-button class="btn" @click="insertFn" variant="info">1</b-button>
      <b-button class="btn" @click="insertFn" variant="info">2</b-button>
      <b-button class="btn" @click="insertFn" variant="info">3</b-button>
      <b-button class="btn" @click="addFn" variant="info">+</b-button>
      <b-button class="btn" @click="percentageFn" variant="info">%</b-button>
      <b-button class="btn zero-btn" @click="insertFn" variant="info"
        >0</b-button
      >
      <b-button class="btn" @click="decimalFn" variant="info">.</b-button>
      <b-button class="btn" @click="performFn" variant="info">=</b-button>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'digit',
    'insertFn',
    'addFn',
    'subtractFn',
    'multiplyFn',
    'divisionFn',
    'performFn',
    'decimalFn',
    'negPosFn',
    'percentageFn',
    'clearFn',
    'deleteFn'
  ],
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
.control-container {
  height: 80vh;
  background-color: #45969b;
  display: grid;

  .grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 0.5rem;

    .btn {
      padding: 2rem;
      font-size: 3rem;
      background-color: #50b6bb;
      color: #f2eaec;
    }
  }
}
</style>
