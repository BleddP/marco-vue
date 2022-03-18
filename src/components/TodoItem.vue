<template>
  <div>
    <h1>{{ item.title }}</h1>
    <h2 :class="completedItem ? 'green' : 'red'" @dblclick="reverseCompleted">Completed? {{ completedItem }}</h2>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    item: Object,
  },
  data() {
      return {
          completedItem: this.item.completed
      }
  },
  methods: {
      reverseCompleted() {
          this.completedItem = !this.completedItem
      }
  }
};
</script>

<style scoped>
h2 {
    background: rgb(219, 203, 203);
    width: fit-content;
}

.green {
    color: green;
}

.red {
    color: red;
}
</style>