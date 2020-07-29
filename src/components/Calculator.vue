<template>
  <div class="container wrap">
    <div class="disp">{{calculation.current || '0'}}</div>
    <div @click="push(7)" class="btn btn-warning btns number">7</div>
    <div @click="push(8)" class="btn btn-warning btns number">8</div>
    <div @click="push(9)" class="btn btn-warning btns number">9</div>
    <div @click="divide" class="btn btn-warning btns operator">&divide;</div>
    <div @click="push(4)" class="btn btn-warning btns number">4</div>
    <div @click="push(5)" class="btn btn-warning btns number">5</div>
    <div @click="push(6)" class="btn btn-warning btns number">6</div>
    <div @click="multiply" class="btn btn-warning btns operator">&times;</div>
    <div @click="push(1)" class="btn btn-warning btns number">1</div>
    <div @click="push(2)" class="btn btn-warning btns number">2</div>
    <div @click="push(3)" class="btn btn-warning btns number">3</div>
    <div @click="plus" class="btn btn-warning btns operator">+</div>
    <div @click="clear" class="btn btn-warning btns operator">C</div>
    <div @click="push(0)" class="btn btn-warning btns number">0</div>
    <div @click="equals" class="btn btn-warning btns operator">=</div>
    <div @click="minus" class="btn btn-warning btns operator">&minus;</div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      calculation: {
        previous: null,
        current: "",
        operator: null,
        click: false,
        symbol: "",
        end: false
      }
    };
  },
  methods: {
    clear() {
      this.calculation.current = "";
    },
    last() {
      this.calculation.previous = this.calculation.current;
      this.calculation.click = true;
    },
    divide() {
      this.calculation.operator = (a, b) => a / b;
      this.last();
      this.calculation.current = "";
      this.calculation.symbol = "÷";
    },
    multiply() {
      this.calculation.operator = (a, b) => a * b;
      this.last();
      this.calculation.current = "";
      this.calculation.symbol = "x";
    },
    minus() {
      this.calculation.operator = (a, b) => a - b;
      this.last();
      this.calculation.current = "";
      this.calculation.symbol = "-";
    },
    plus() {
      this.calculation.operator = (a, b) => a + b;
      this.last();
      this.calculation.current = "";
      this.calculation.symbol = "+";
    },
    equals() {
      this.calculation.current = this.calculation.operator(
        parseFloat(this.calculation.previous),
        parseFloat(this.calculation.current)
      );
      this.calculation.prev = null;
      this.calculation.symbol = "";
      this.calculation.end = true;
    },
    push(num) {
      let result = `${this.calculation.current}${num}`;
      if (num == "0" && this.calculation.current == "") {
        this.calculation.current = "";
      } else {
        if (this.calculation.click) {
          this.calculation.current = "";
          this.calculation.click = false;
        }
        this.calculation.current = result;
      }
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.btns {
  width: 20% !important;
  margin: 3px !important;
}

.number {
  background-color: lightblue !important;
  border: lightblue !important;
}

.operator {
  background-color: lightgray !important;
  border: lightgray !important;
}

.wrap {
  width: 40% !important;
}

.disp {

}
</style>
