<template>
  <h2>{{name}}</h2>
  <h2>{{age}}</h2>
  <h2>{{dog}}</h2>
  <p>{{sentence}}</p>
</template>

<script>
export default {
    name: "NewComponent",
    props: {
        person: Object,
    },
    data() {
        return {
            name: this.person.name,
            age: this.person.age,
            dog: this.person.dog,
        }
    },
    computed: {
        sentence() {
            return `Hallo, ik ben ${this.person.name}, ik ben ${this.person.age} jaar en heb een hond die ${this.person.dog} heet.`
        }
    }

}
</script>