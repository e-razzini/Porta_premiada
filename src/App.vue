<template>
  <div id="app">
    <h1>problema monty hall</h1>
    <Door numero="1" :hasGift="false" />
  </div>
</template>

<script>
import Door from "./components/Door";
export default {
  name: "app",
  components: { Door },
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Titillium Web", sans-serif;
}
body {
  color: #fff;
  background: linear-gradient(
    90deg,
    rgba(180, 58, 93, 1) 10%,
    rgba(253, 71, 29, 0.9575980050223214) 50%,
    rgba(252, 97, 69, 1) 75%
  );
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
#app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 20px;
  margin-bottom: 60px;
}
</style>