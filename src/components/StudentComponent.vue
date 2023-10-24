<template>
  <div>
    <!-- <div>{{ id }}. {{ name }}</div>
    <q-icon name="delete" size="32px" @click="removeStd(id)"></q-icon> -->
    <CardSlot>
      <template #card-header> Student No. {{ id }} </template>
      <template #card-content> {{ name }} </template>
      <template #card-footer>
        <q-icon name="delete" size="32px" color="white" @click="removeStd(id)">
        </q-icon>
      </template>
    </CardSlot>
  </div>
</template>
<script>
import { defineComponent } from "vue";
import CardSlot from "./CardSlot.vue";
export default defineComponent({
  name: "StudentComponent",
  props: {
    id: {
      type: Number,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
  },
  methods: {
    removeStd(id) {
      this.$emit("del", id);
    },
  },
  components: { CardSlot },
});
</script>
