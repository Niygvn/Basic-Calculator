<template>
  <div class="container">
    <input type="text" class="result" readonly />
    <div class="buttons">
      <button class="clear">C</button>
      <button class="operator">/</button>
      <button class="operator">*</button>
      <button class="operator">-</button>
      <button class="number">7</button>
      <button class="number">8</button>
      <button class="number">9</button>
      <button class="operator">+</button>
      <button class="number">4</button>
      <button class="number">5</button>
      <button class="number">6</button>
      <button class="operator">%</button>
      <button class="number">1</button>
      <button class="number">2</button>
      <button class="number">3</button>
      <button class="operator">ₓʸ</button>
      <button class="number">0</button>
      <button class="decimal">.</button>
      <button class="decimal">(</button>
      <button class="delete">Del</button>
      <button class="decimal">)</button>
      <button class="equals">Calculate</button>
    </div>
  </div>
</template>
<script setup>
import { onMounted } from "vue";

let inputResult = null;
let buttons = null;

onMounted(() => {
  inputResult = document.getElementsByClassName("result");
  //console.log(inputResult);
  buttons = document.querySelectorAll("button");
  //console.log(buttons);
  buttons.forEach((button) => {
    button.addEventListener("click", () => {
      if (button.innerHTML === "Calculate") {
        inputResult[0].value = eval(inputResult[0].value);
      } else if (button.innerHTML === "ₓʸ") {
        inputResult[0].value += "**";
      } else if (button.innerHTML === "C") {
        inputResult[0].value = "";
      } else if (button.innerHTML === "Del") {
        let arr = inputResult[0].value.split("");
        arr.pop();
        let str = arr.join("");
        inputResult[0].value = str;
      } else {
        inputResult[0].value += button.innerHTML;
      }
    });
  });
});
</script>
