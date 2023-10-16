<template>
  <q-page padding>
    <div>
      <q-input color="blue" v-model="value1" label="Enter number"> </q-input>
      {{ value1 }} x 2 = {{ result }}
    </div>
    <div>
      <q-input color="teal" filled v-model="mySearch" label="Type to search">
        <template v-slot:prepend>
          <q-icon name="zoom_out" />
        </template>
      </q-input>
    </div>
    <div class="listItem" v-for="result in getSearchResult" :key="result.id">
      {{ result.label }}
    </div>
    <div>
      Method Section
      <ul>
        <li v-for="val in 3" :key="val">
          {{ getRandomMethod() }}
        </li>
      </ul>
    </div>
    <div>
      Compute Section
      <ul>
        <li v-for="val in 3" :key="val">
          {{ getRandomComputed }}
        </li>
      </ul>
    </div>
    <div>{{ name }}</div>
    <div>My age is {{ age }}</div>
    <div>
      <q-btn color="primary" label="Increment" @click="age++" />
      <q-btn color="amber" glossy label="Decrement" @click="age--" />
      <q-btn color="secondary" label="+10" @click="age += 10" />
    </div>
    <div>
      My GPA is
      {{ gpa }}
    </div>
    <div>Address: <span v-html="address"></span></div>
    <ul>
      <li v-for="(val, key) in hobbies" :key="key">{{ val }}</li>
    </ul>
    <ul v-if="showinfo">
      <li v-for="(val, property, index) in info" :key="index">
        {{ val }}{{ property }}{{ index }}
      </li>
    </ul>
    <div v-else>No Information</div>
    <div>Status: {{ getStatus() }}</div>
    <div class="q-pa-lg">
      <q-option-group
        v-model="qOptionGroup"
        :options="qOptionObj"
        color="primary"
        type="toggle"
      />
      <div>Selection is {{ qOptionGroup }}</div>
      <q-select
        v-model="qselect"
        :options="options"
        label="Select Your Social Media"
      />
      <div>Your social media is {{ qselect }}</div>
      <q-input
        v-model="text"
        label="Type Something Here"
        placeholder="Hello!"
        :dense="dense"
        @keyup.enter="clearText"
      />
      <q-btn class="pa" color="purple" label="Clear Text" @click="clearText" />
      <div>Textbox: {{ text }}</div>
    </div>
    <q-img :src="url" spinner-color=" white" :ratio="1">
      <div class="absolute-top text-center">This is my caption</div>
    </q-img>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  data() {
    return {
      name: "myName",
      age: 10,
      gpa: 2.25,
      address: "<i>Phuket<i/>",
      hobbies: ["Running", "Swimming", "Playing Cardgame"],
      info: {
        gender: "not specific",
        weight: 111,
        height: 222.3,
      },
      url: "https://en.cf-vanguard.com/wordpress/wp-content/images/cardlist/vbt10/vbt10_001.png",
      showInfo: true,
      text: null,
      qselect: null,
      options: ["FB", "X", "IG"],
      qOptionGroup: [],
      qOptionObj: [
        {
          label: "Milk Tea",
          value: "0",
          color: "red",
        },
        {
          label: "Grean Tea",
          value: "1",
          color: "yellow",
        },
        {
          label: "Black Tea",
          value: "2",
          color: "blue",
        },
      ],
      fruits: [
        { id: 1, label: "Banana" },
        { id: 2, label: "Apple" },
        { id: 3, label: "Orange" },
      ],
      mySearch: null,
    };
  },
  methods: {
    getStatus() {
      return this.gpa >= 2.0 ? this.addition(10) : "Fail";
    },
    addition(params) {
      return this.gpa + params;
    },
    incremental(param) {
      this.age += param;
    },
    clearText() {
      this.text = "";
    },
    getRandomMethod() {
      return Math.random();
    },
  },
  computed: {
    getRandomComputed() {
      return Math.random();
    },
    getSearchResult() {
      if (this.mySearch)
        return this.fruits.filter((item) =>
          item.label
            .toString()
            .toLowerCase()
            .includes(this.mySearch.toString().toLowerCase())
        );
      else return this.fruits;
    },
  },
  watch: {
    value1() {
      this.result = 2 * this.value1;
    },
  },
});
</script>
<style scoped>
.listItem {
  padding: 10px;
  margin: 10px;
  border-radius: 10px;
  background-color: greenyellow;
}
</style>
