<template>
  <div class="container">
    <header class="display">{{ curr || '0' }}</header>
    <button @click="clear()" class="op op-ac">AC</button>
    <button @click="negative()" class="op op-neg">+/-</button>
    <button @click="percent()" class="op op-percent">%</button>
    <button @click="divide()" class="op op-main op-divide">÷</button>
    <button @click="times()" class="op op-main op-multi">×</button>
    <button @click="minus()" class="op op-main op-minus">−</button>
    <button @click="plus()" class="op op-main op-plus">+</button>
    <button @click="equals()" class="op op-main op-eql">=</button>
    <button @click="dot()" class="num-dot">.</button>

    <button @click="push(0)" class="num-0">0</button>
    <button @click="push(1)" class="num-1">1</button>
    <button @click="push(2)" class="num-2">2</button>
    <button @click="push(3)" class="num-3">3</button>
    <button @click="push(4)" class="num-4">4</button>
    <button @click="push(5)" class="num-5">5</button>
    <button @click="push(6)" class="num-6">6</button>
    <button @click="push(7)" class="num-7">7</button>
    <button @click="push(8)" class="num-8">8</button>
    <button @click="push(9)" class="num-9">9</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      prev: null,
      curr: "",
      op: null,
      opClicked: false,
    };
  },

  methods: {
    clear() {
      this.curr = "";
    },

    push(num) {
      if (this.opClicked) {
        this.curr = "";
        this.opClicked = false;
      }
      this.curr = `${this.curr}${num}`;
    },

    negative() {
      this.curr = this.curr.charAt(0) === "-" 
      ? this.curr.slice(1) 
      : `-${this.curr}`;
    },

    percent() {
      this.curr = `${parseFloat(this.curr) / 100}`;
    },

    divide() {
      this.op = (a, b) => a / b;
      this.setPrev();
      this.opClicked = true;
    },

    times() {
      this.op = (a, b) => a * b;
      this.setPrev();
      this.opClicked = true;
    },

    minus() {
      this.op = (a, b) => a - b;
      this.setPrev();
      this.opClicked = true;
    },

    plus() {
      this.op = (a, b) => a + b;
      this.setPrev();
      this.opClicked = true;
    },

    equals() {
      this.curr = `${this.op(parseFloat(this.prev), parseFloat(this.curr))}`
      this.prev = null
    },
    
    dot() {
      if (this.curr.indexOf(".") === -1) {
        this.push(".");
      }
    },

    setPrev() {
      this.prev = this.curr;
      this.opClicked = true;
    },
  },
};
</script>

<style scoped>
body {
  font-family: "Roboto", sans-serif;
  color: #343a40;
}
.container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 340px;
  height: 520px;
  display: grid;
  grid-template-rows: 110px repeat(5, 1fr);
  grid-template-columns: repeat(4, 1fr);
  grid-template-areas:
    "display display display display"
    "btn-ac btn-neg btn-perc op-div"
    "num-7 num-8 num-9 op-mult"
    "num-4 num-5 num-6 op-min"
    "num-1 num-2 num-3 op-plus"
    "num-0 num-0 num-dot op-eql";
  box-shadow: 1px 1px 4px #e0e0e0;
}

.display {
  margin: 0;
  padding: 20px;
  background: #a5a5a5ce;
  font-size: 4em;
  grid-area: display;
  line-height: 1.6;
  text-align: right;
}

button {
  border-width: 0;
  font-size: 2em;
  background: #e9ecef;
}

button:active {
  background: #8d9094ce;
}

.op {
  background: #ced4da;
  color: #868e96;
}

.op-main {
  font-size: 2.5em;
  color: #343a40;
}

.op-ac {
  grid-area: btn-ac;
  background: #42b883;
  color: #f8f9fa;
}

.op-neg {
  grid-area: btn-neg;
}

.op-percent {
  grid-area: btn-perc;
}

.op-divide {
  grid-area: op-div;
}

.op-multi {
  grid-area: op-mult;
}

.op-min {
  grid-area: minus;
}

.num-7 {
  grid-area: num-7;
}

.num-8 {
  grid-area: num-8;
}

.num-9 {
  grid-area: num-9;
}

.num-4 {
  grid-area: num-4;
}

.num-5 {
  grid-area: num-5;
}

.num-6 {
  grid-area: num-6;
}

.op-min {
  grid-area: op-min;
}

.num-1 {
  grid-area: num-1;
}

.num-2 {
  grid-area: num-2;
}

.num-3 {
  grid-area: num-3;
}

.op-plus {
  grid-area: op-plus;
}

.num-0 {
  grid-area: num-0;
}

.num-dot {
  grid-area: num-dot;
}

.op-eql {
  grid-area: op-eql;
}
</style>
