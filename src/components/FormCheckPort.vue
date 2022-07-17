<script>
import ResultFinal from "./ResultFinal.vue";

import { ref } from "vue";
export default {
  name: "FormCheckPort",
  components: {
    ResultFinal,
  },

  data() {
    return {
      port: ref(),
      ip: "192.168.1.25",
      show: false,
      nowPort: "",
    };
  },
  methods: {
    resultPort() {
      if (this.port === "" || this.ip === "") {
        this.show = false;
        return false;
      }
      this.nowPort = this.port;
      this.show = true;
    },
    getIP() {
      fetch("https://api.ipify.org?format=json")
        .then((x) => x.json())
        .then(({ ip }) => {
          this.ip = ip;
        });
    },
  },
  mounted() {
    this.getIP();
  },
};
</script>

<template>
  <div class="container">
    <h4>Checa Porta Aberta - CheckPort</h4>
    <div class="box-form">
      <label>IP</label>
      <input type="text" v-model="ip" name="ip" />
      <label>Port</label>
      <input type="text" name="port" v-model="port" />
      <input type="submit" value="Testar" @click.prevent="resultPort" />
    </div>
    <ResultFinal :port="nowPort" v-if="show" />
  </div>
</template>

<style scoped>
.container {
  background: var(--bg-color);
  max-width: 468px;
  min-width: 200px;
  min-height: 596;
  padding: 1em 2em;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.7);
  border-radius: 4px;
}
.box-form {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4em;
  margin-top: 10px;
  align-items: flex-end;
}

.box-form input {
  border-style: none;
  padding: 8px 4px;
  border-radius: 4px;
  margin-top: 6px;
}
.box-form input:nth-child(4) {
  width: 60px;
  margin-right: 5px;
}
.box-form input:nth-child(2) {
  margin-right: 5px;
}
.box-form input[type="submit"] {
  font-weight: bold;
  padding: 8px 16px;
  color: var(--bg-color);
}
.box-form input[type="submit"]:hover {
  box-shadow: 0px 0px 4px rgba(255, 255, 255, 0.9);
  color: var(--bg-color);
}
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
