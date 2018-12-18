<template>
<div class="calculator">
        <h1>Calculator</h1>
        <h1>{{ current }}</h1>
        <h2>{{ total}}</h2>
        <section>
          <button v-on:click="current = 0, total = 0, selected = null">AC</button>
          <button v-on:click="current = -current">+/-</button>
          <button v-on:click="current = Number(current) * 0.01">%</button>
        </section>
          <button
           v-for="(operator, index) in operators" 
           :key="index"
           v-on:click="calculate(operator)"
           >
           {{ operator }}           
           </button>
           <button v-on:click="calculate()">=</button>
        <!-- <span v-if="selected">ans={{ answer }}</span> -->
        <section>
          <button          
          v-for="(digit, index) in [0,1,2,3,4,5,6,7,8,9]"
          :key="index"
          v-on:click="current === 0 ? current = String(digit) : current += digit"
          >
          {{ digit }}
          </button>
          <button v-on:click="current.toString().indexOf('.') == -1 ? current += '.' : null">.</button>
        </section>
        
    </div>
</template>

<script>
export default {
  name: "BubbleCalculator",
  data() {
    return {
      current: 0,
      total: 0,
      operators: ["+", "-", "*", "/"],
      selected: null
    };
  },
  computed: {
    answer: function() {
      let currentNumber = Number(this.current);
      let ans = 0;
      console.log(
        "in answer...this.current",
        this.current,
        "this.total",
        this.total
      );
      if (this.selected === "+") {
        console.log("+", currentNumber, this.total, currentNumber + this.total);
        ans = currentNumber + this.total;
      } else if (this.selected === "-") {
        ans = currentNumber - this.total;
      } else if (this.selected === "*") {
        ans = currentNumber * this.total;
      } else if (this.selected === "/") {
        ans = currentNumber / this.total;
      }
      console.log("answer...", this.selected, ans);
      return ans;
    }
  },
  methods: {
    updateTotal: function() {
      console.log(
        "in updateTotal",
        "this.total= ",
        this.total,
        "this.answer= ",
        this.answer
      );
      this.total = this.answer;
      console.log(
        "in updateTotal",
        "this.total= ",
        this.total,
        "this.answer= ",
        this.answer
      );
    },
    calculate: function(symbol = null) {
      this.updateTotal();
      this.selected = symbol;
      this.current = "0";
    }
  }
};
</script>

<style scoped>
</style>
