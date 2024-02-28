<template>
  <section>
    <article>
      <h1>Content</h1>
    </article>

    <select v-model="selected">
      <option v-for="option in options" :value="option.value">
        {{ option.text }}
      </option>
    </select>

    <div>Selected: {{ selected }}</div>
    

    <div>
      <p>message: {{ message }}</p>
      <input v-model="message" type="text" placeholder="input message" />
      <input type="checkbox" v-model="checked" />
    </div>
    <div>Checked names: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
    <label for="jack">Jack</label>

    <input type="checkbox" id="john" value="John" v-model="checkedNames" />
    <label for="john">John</label>

    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
    <label for="mike">Mike</label>

    <section>
      <article>
        <h3>List Render</h3>
      </article>
      <main v-for="(item, index) in items" :key="index">
        <p>id: {{ item.id }}</p>
        <p>Name: {{ item.name }}</p>
        <p>Sex: {{ item.sex }}</p>
      </main>

      <main v-for="numners in sets">
        <p v-for="n in evenNumber(numners)">{{ n }}</p>
      </main>
    </section>

    <main>
      <h4>Condintional in vuejs</h4>
      <button @click="awesome = !awesome">Toggle</button>

      <h1 v-if="awesome">Vue is awesome!</h1>
      <h1 v-else>Oh no 😢</h1>

      <p>Developer</p>

      <span>{{ developer.name }}</span> <br />
      <span>{{ developer.techStack.length > 0 ? "Yes" : "No" }}</span
      ><br />
      <span>msg: {{ msg }}</span>
      <!-- <p>{{ counter }}</p>
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
      <button @click="state.count++">count</button>
      <p>{{ state.count }}</p> -->
    </main>
  </section>
</template>

<script setup>
import { nextTick, reactive, ref, computed } from "vue";

const message = ref("");
const checked = ref(true);
const checkedNames = ref([]);
const selected = ref("A");

const options = ref([
  { text: "One", value: "A" },
  { text: "Two", value: "B" },
  { text: "Three", value: "C" },
]);

const sets = ref([
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10],
]);
const evenNumber = (numbers) => {
  return numbers.filter((number) => number % 2 === 0);
};
const items = ref([
  { id: 1, name: "Kai", sex: "Male" },
  { id: 2, name: "Bright", sex: "Male" },
  { id: 3, name: "Yuzi", sex: "Female" },
]);
const awesome = ref(true);
const developer = reactive({
  name: "Kai",
  techStack: ["HTML5"],
});

const msg = computed(() => {
  return developer.techStack.length > 0 ? "Yes" : "No";
});
// const state = reactive({ count: 0})
// const counter = ref(0);
// const increment = async () => {
//   counter.value++;
//   await nextTick
// };
// const decrement = () => {
//   counter.value--;
// };
</script>

<style lang="css" scoped>
button {
  margin-left: 2rem;
  cursor: pointer;
  padding: 10px;
}
</style>
