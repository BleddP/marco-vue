<template>
  <input type="text" placeholder="search items" @input="inputChange($event)" />
</template>

<script>
export default {
    name: "Searchbar",
    data() {
        return {
            searchQuery: ''
        }
    }, 
    methods: {
        inputChange(event) {
            const input = event.target.value
            this.$emit("letsChangeTheInput", input)
        }
    }
    
}
</script>