<template>
  <div class="wrap">
    <div class="calculator">
      <div id="display" class="btn">0.6523</div>
      <div id="clear" class="btn">C</div>
      <div id="sign" class="btn">+/-</div>
      <div id="percent" class="btn">%</div>
      <div id="divide" class="btn operator">&#247</div>
      <div id="seven" class="btn">7</div>
      <div id="eight" class="btn">8</div>
      <div id="nine" class="btn">9</div>
      <div id="multiply" class="btn operator">x</div>
      <div id="four" class="btn">4</div>
      <div id="five" class="btn">5</div>
      <div id="six" class="btn">6</div>
      <div id="subtract" class="btn operator">-</div>
      <div id="one" class="btn">1</div>
      <div id="two" class="btn">2</div>
      <div id="three" class="btn">3</div>
      <div id="add" class="btn operator">+</div>
      <div id="zero" class="btn">0</div>
      <div id="decimal" class="btn">.</div>
      <div id="equals" class="btn operator">=</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  props: {
    msg: String
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
.operator {
  background-color: orange;
  color: $White;
}
</style>
