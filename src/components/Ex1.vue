<script>
export default {
  name: "Ex1",
  data() {
    return {
      x: 0,
      y: 0,
      operators: ["+", "-", "*", "/", "%"],
      selectedOp: ""
    };
  },
  computed: {
    result() {
      const x = Number(this.x);
      const y = Number(this.y);

      switch (this.selectedOp) {
        case "+": return x + y;
        case "-": return x - y;
        case "*": return x * y;
        case "/": return x / y;
        case "%": return x % y;
      }
    }
  }
};
</script>

<template>
    <p>x <input v-model.number="x"></p>
    <select v-model="selectedOp">
        <option v-for="op in operators" >{{ op }}</option>
    </select>
    <p>y <input v-model.number="y"></p>
    
    <p>---------------------</p>

    <p>= {{result}}</p>
</template>

<style scoped>
    p, input { font-family: monospace; }
    p { white-space: pre; }

</style>
