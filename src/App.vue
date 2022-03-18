<template>
  <div>
    <Searchbar @letsChangeTheInput="pleaseFilterItems" />
    <h1 v-if="loading">Loading....</h1>
    <div v-else>

      <TodoItem v-for="item in filteredItems" :key="item.id" :item="item" />

    </div>
  </div>
</template>

<script>
import axios from "axios";
import TodoItem from "./components/TodoItem.vue";
import Searchbar from "./components/Searchbar.vue";

export default {
  name: "App",

  data() {
    return {
      loading: true,
      items: [],
      error: "",
      orignalInputState: ""
    };
  },
  components: {
    TodoItem,
    Searchbar
  },
  methods: {
    pleaseFilterItems(userInput) {
      this.orignalInputState = userInput
    }
  },
  computed: {
    filteredItems() {
      return this.items.filter(item => item.title.includes(this.orignalInputState.toLowerCase()))
    }
  },
  async created() {
    this.loading = true;
    this.error = "";

    axios
      .get("https://jsonplaceholder.typicode.com/todos")
      .then((res) => {
        this.items = res.data;
      })
      .catch((error) => {
        console.log("Je hebt een error", error);
        this.items = [];
        this.error = "OOps, niks gevonden";
      })
      .finally(() => {
        this.loading = false;
      });
  },
};
</script>
