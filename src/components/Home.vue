<template>
  <div>{{ data }}</div>
</template>
<script>
import { ref } from "vue";
import jsonData from "../da.json";

export default {
  setup() {
    const data = ref(null);
    data.value = jsonData;
  },
};
</script>
