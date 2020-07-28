<template>
  <div class="calculator-container">
    <app-display :digit="digit" :displayVal="displayVal"></app-display>
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
      :deleteFn="deleteOperation"
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
      pendingVal: '',
      digitArray: [],
      displayVal: ''
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
      this.digit = '';
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('+');
      this.displayVal = this.digitArray.join(' ');
    },
    subtractOperation() {
      this.pendingVal = this.digit;
      this.digit = '';
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('-');
      this.displayVal = this.digitArray.join(' ');
    },
    multiplicationOperation() {
      this.pendingVal = this.digit;
      this.digit = '';
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('*');
      this.displayVal = this.digitArray.join(' ');
    },
    divisionOperation() {
      this.pendingVal = this.digit;
      this.digit = '';
      this.digitArray.push(this.pendingVal);
      this.digitArray.push('/');
      this.displayVal = this.digitArray.join(' ');
    },
    decimalOperation(value) {
      if (this.digit.toString().includes('.')) {
        return this.digit;
      }
      let currentValue = this.digit;
      let newValue = value.target.innerText;
      currentValue += newValue;
      this.digit = currentValue;
    },
    performOperation() {
      this.digitArray.push(this.digit);
      const evaluation = eval(this.digitArray.join(' '));
      this.digit = evaluation;
      this.displayVal = this.digitArray.join(' ');
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
      this.displayVal = '';
      this.pendingVal = '';
    },
    deleteOperation() {
      if (this.digit !== 0) {
        this.digit = this.digit.substring(0, this.digit.length - 1);
      }
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
