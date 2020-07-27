<template>
  <div class="calculator-container">
    <app-display :digit="digit"></app-display>
    <app-control
      :digit="digit"
      :insertFn="insert"
      :addFn="addOperation"
      :subtractFn="subtractOperation"
      :multiplyFn="multiplicationOperation"
      :divisionFn="divisionOperation"
      :performFn="performOperation"
      :decimalFn="decimalOperation"
      :negPosFn="negPosOperation"
      :percentageFn="percentageOperation"
      :clearFn="clearField"
    ></app-control>
  </div>
</template>

<script>
import Display from '../components/Display';
import Control from '../components/Controls';

export default {
  data() {
    return {
      digit: 0,
      digitArray: []
    };
  },
  methods: {
    insert(value) {
      let currentValue = this.digit;
      let newValue = value.target.innerText;
      if (currentValue === 0) {
        currentValue = '';
      }
      currentValue += newValue;
      this.digit = currentValue;
    },
    addOperation() {
      this.pendingVal = this.digit;
      this.digit = 0;
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('+');
    },
    subtractOperation() {
      this.pendingVal = this.digit;
      this.digit = 0;
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('-');
    },
    multiplicationOperation() {
      this.pendingVal = this.digit;
      this.digit = 0;
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('*');
    },
    divisionOperation() {
      this.pendingVal = this.digit;
      this.digit = 0;
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('/');
    },
    decimalOperation(value) {
      let oldValue = '';
      if (this.digit === 0) {
        oldValue = this.digit + value.target.innerText;
      } else {
        oldValue = this.digit + value.target.innerText;
      }
      if (this.digit.toString().includes('.')) {
        return oldValue;
      }
      this.digit = oldValue;
      console.log(this.digitArray);
    },
    performOperation() {
      this.digitArray.push(this.digit);
      const evaluation = eval(this.digitArray.join(' '));
      this.digit = evaluation;
      this.digitArray = [];
    },
    negPosOperation() {
      if (Math.sign(this.digit) === 1) {
        this.digit = -Math.abs(this.digit);
      } else if (Math.sign(this.digit) === -1) {
        this.digit = Math.abs(this.digit);
      }
    },
    percentageOperation() {
      const oldValue = this.digit;
      if (oldValue !== 0) {
        let newValue = oldValue / 100;
        this.digit = newValue;
      }
    },
    clearField() {
      this.digit = 0;
      this.digitArray = [];
    }
  },
  components: {
    appDisplay: Display,
    appControl: Control
  }
};
</script>

<style lang="scss" scoped>
.calculator-container {
  height: 100vh;
}
</style>
