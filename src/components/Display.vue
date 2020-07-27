<template>
  <div class="display-container">
    <p>{{ digit }}</p>
  </div>
</template>

<script>
export default {
  props: ['digit']
};
</script>

<style lang="scss" scoped>
.display-container {
  height: 20vh;
  background-color: #0a1826;
  display: flex;
  justify-content: flex-end;
  align-items: center;

  p {
    font-size: 7rem;
    color: #f2eaec;
    margin: 1rem;
  }
}
</style>
