<template>
  <main>
    <h1>Hello world!</h1>
  </main>
</template>
<script>
import axios from "axios";
axios.defaults.headers.common["default-header"] = "default-header";

export default {
  async fetch({ $axios }) {
    axios
      .get("https://jsonplaceholder.typicode.com/todos/1", {
        headers: { header1: "header1" },
      })
      .then((response) => {
        console.error(response.config);
      });
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos/1", {
        headers: { header1: "header1" },
      })
      .then((response) => {
        console.error(response.config);
      });
  },
};
</script>
