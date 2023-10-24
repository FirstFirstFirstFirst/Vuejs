<template>
  <q-page padding>
    <div>
      <h5>This is Page 1</h5>
    </div>
    <div>
      <h2>My counter: {{ mystore.counter }}</h2>
    </div>
  </q-page>
</template>
<script>
import { defineComponent } from "vue";
import { useCounterStore } from "stores/counter";
export default defineComponent({
  name: "PiniaPage1",
  data() {
    return {
      mystore: useCounterStore(),
    };
  },
});
</script>
