<template>
  <div class="result">
    <p>Resultado:</p>
    <div class="result-port">
      <p>{{ newPort }}</p>
      <p>Open/Aberta</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResultFinal",
  props: {
    port: String,
  },
  beforeUpdate() {
    this.newPort = this.port;
  },
  created() {
    this.newPort = this.port;
  },
  data() {
    return {
      newPort: this.port,
    };
  },
};
</script>

<style>
.result {
  text-align: left;
  margin-top: 20px;
}
.result-port {
  padding: 2em 0;
}

.result-port > p {
  width: 200px;
  margin: 0 auto;
  text-align: center;
  border-radius: 4px;
  font-weight: bold;
  background: green;
}
.result-port > p:nth-child(1) {
  padding-top: 1em;
}
.result-port > p:nth-child(2) {
  padding-bottom: 1em;
}
</style>
