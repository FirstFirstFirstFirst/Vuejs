<template>
  <q-page padding>
    <h6>This is main component page</h6>
    <MyComponent></MyComponent>
  </q-page>
</template>
<script>
import { defineComponent } from "vue";
import MyComponent from "../components/MyComponent.vue";
export default defineComponent({
  name: "MainComponentPage",
  components: { MyComponent },
});
</script>
