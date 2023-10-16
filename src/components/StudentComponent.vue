<template>
  <div>My name is {{ name }}</div>
</template>
<script>
import { defineComponent } from "vue";
export default defineComponent({
  name: "StudentComponent",
  props: ["name"],
});
</script>
