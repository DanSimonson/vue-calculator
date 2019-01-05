<template>
  <div class="wrap">
    <div class="calculator">
      <div id="display" class="btn">{{result || 0}}</div>
      <div @click="clear()" id="clear" class="btn">C</div>
      <!--<div @click="number('1')" id="sign" class="btn">+/-</div>
      <div @click="unique('%')" id="percent" class="btn">%</div>-->
      <div @click="math('/' )" id="divide" class="btn operator">&#247</div>
      <div @click="number('7')" id="seven" class="btn">7</div>
      <div @click="number('8')" id="eight" class="btn">8</div>
      <div @click="number('9')" id="nine" class="btn">9</div>
      <div @click="math('*')" id="multiply" class="btn operator">&#215;</div>
      <div @click="number('4')" id="four" class="btn">4</div>
      <div @click="number('5')" id="five" class="btn">5</div>
      <div @click="number('6')" id="six" class="btn">6</div>
      <div @click="math('-')" id="subtract" class="btn operator">&#8722;</div>
      <div @click="number('1')" id="one" class="btn">1</div>
      <div @click="number('2')" id="two" class="btn">2</div>
      <div @click="number('3')" id="three" class="btn">3</div>
      <div @click="math('+')" id="add" class="btn operator">&#43;</div>
      <div @click="number('0')" id="zero" class="btn">0</div>
      <div @click="unique('.')" id="decimal" class="btn">.</div>
      <div @click="equal" id="equals" class="btn operator">=</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  props: {
    msg: String
  },
  data() {
    return {
      result: "",
      results: []
    };
  },
  methods: {
    number(item) {
      //number not allowed to start with multiple zeros
      if (item === "0" && this.result.length < 2) {
        this.result = "0";
      } else {
        this.result += item;
      }
    },
    math(operator) {
      //get last char in data string
      const lastChar = this.result[this.result.length - 1];
      //check if last character is an operand
      const bool = ["*", "+", "-", "/"].includes(lastChar);
      if (bool) {
        //remove last char since it is operand
        this.result = this.result.slice(0, -1);
        //replace with new operand
        this.result += operator.toString();
      } else {
        //just append operand
        this.result += operator.toString();
      }
    },
    unique(operator) {
      //two '.' operators will not be accepted in one number
      if (this.result.includes(".") === false) {
        this.result += operator.toString();
      }
    },
    equal() {
      let result = this.result;
      let total = math.eval(result);
      this.results.push({ math: result, total: result });
      this.result = total;
    },
    clear() {
      this.result = "";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../public/styles.scss";

.wrap {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn {
  background-color: #f2f2f2;
  border: 1px solid #999;
  display: flex;
  justify-content: center;
  align-items: center;
}
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  margin: 0 auto;
  width: 500px;
  font-size: 20px;
}
#clear {
}
#display {
  grid-column: 1/5;
  background-color: $Black;
  color: $White;
  display: flex;
  justify-content: flex-end;
  font-size: 1.5rem;
  padding: 10px;
}
#zero {
  grid-column: 1/3;
  text-align: center;
}
#clear {
  grid-column: 1/4;
  text-align: center;
}
.operator {
  background-color: orange;
  color: $White;
}
</style>
