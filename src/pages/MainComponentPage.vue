<template>
  <q-page padding>
    <h6>This is main component page</h6>

    <StudentComponent
      v-for="(item, key) in students"
      :key="key"
      :id="item.id"
      :name="item.name"
      @del="removeItem"
    ></StudentComponent>
  </q-page>
</template>
<script>
import { defineComponent } from "vue";
// import MyComponent from "../components/MyComponent.vue";
import StudentComponent from "../components/StudentComponent.vue";
export default defineComponent({
  name: "MainComponentPage",
  components: { StudentComponent },
  data() {
    return {
      students: [
        { id: 1, name: "Anya Forger" },
        { id: 2, name: "Loid Forger" },
        { id: 3, name: "Yor Forger" },
      ],
    };
  },
  methods: {
    removeItem(id) {
      this.students = this.students.filter((item) => {
        return item.id != id;
      });
    },
  },
});
</script>
