<template>
  <div class="display-container">
    <span>{{ displayVal }}</span>
    <p>{{ digit }}</p>
  </div>
</template>

<script>
export default {
  props: ['digit', 'displayVal']
};
</script>

<style lang="scss" scoped>
.display-container {
  height: 20vh;
  background-color: #0a1826;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;

  span {
    position: absolute;
    top: 0.5rem;
    right: 3rem;
    font-size: 1.4rem;
    color: #9e9e9e;

    @media screen and (max-width: 400px) {
      font-size: 1.2rem;
    }
  }

  p {
    font-size: 5rem;
    color: #f2eaec;
    margin: 1rem;

    @media screen and (max-width: 450px) {
      font-size: 3rem;
    }
  }
}
</style>
