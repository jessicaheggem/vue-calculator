<template>
  <div>
    <h3>Calculator Challenge</h3>
    <br />
    <div class="container wrap border rounded p-4">
      <input class="disp text-right form-control" :value="calculation.current || '0'" />
      <br />
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
    <br />
    <h5>{{[calculation.previous, calculation.symbol, calculation.current, calculation.end, calculation.operator]}}</h5>
    <button v-on:click="sendMessage('hello')">Send Message</button>
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
      },
    connection: null
    };
  },
  methods: {
    sendMessage: function(message) {
      console.log(this.connection);
      this.connection.send(message);
    },
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
      this.calculation.previous = null;
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
  },
  created: function() {
    console.log("Starting connection to WebSocket Server")
    this.connection = new WebSocket("wss://echo.websocket.org")

    this.connection.onmessage = function(event) {
      console.log(event);
    }

    this.connection.onopen = function(event) {
      console.log(event)
      console.log("Successfully connected to the echo websocket server...")
    }
  },
  
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
  font-size: 20px !important;
}

.number {
  background-color: #6fcfd6 !important;
  border: #6fcfd6 !important;
}

.operator {
  background-color: #b5dadd !important;
  border: #b5dadd !important;
}

.wrap {
  width: 35% !important;
  background-color: #2d5457 !important;
}

.disp {
  font-size: 20px !important;
  background-color: #f2f2f2 !important;
  border: ;
}
</style>
