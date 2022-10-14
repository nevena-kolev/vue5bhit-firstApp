<template>
  <div id="app">
    <h3>Example</h3>

    <form @submit.prevent="addNew">
      <label for="item">Enter new subject: </label>
      <input v-model="newSubject" />
      <button>Add subject</button>
      <hr />
    </form>

    <ul>
      <li v-for="item in subjectArray">
        {{ item.content }} <button @click="deleteItem">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const newSubject = ref(''); // bindings
    const subjectArray = ref([]);

    function addNew() {
      if (newSubject.value !== '') {
        subjectArray.value.push({ content: newSubject.value });
        newSubject.value = '';
      }
    }

    function deleteItem() {
      const found = subjectArray.value.find(
        (element) => element == newSubject.value
      );
      console.log(found);
      subjectArray.value.pop(found);
    }

    return {
      newSubject,
      subjectArray,
      addNew,
      deleteItem,
    };
  },
};

// delete-button neben jeden eintrag
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
