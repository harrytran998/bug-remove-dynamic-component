<template>
  <div id="app">
    <template v-for="(child, index) in children">
      <component
        :is="child"
        :key="index"
        :index-form="index"
        :age="ages[index]"
        @deleteForm="deleteForm($event)"
      />
    </template>
    <button @click="add()">Add Another</button>
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form,
  },
  created() {
    const ageLength = this.ages.length
    for (let i = 0; i < ageLength; i++) {
      this.children.push(Form)
    }
    console.log(this.children)
  },
  data() {
    return {
      children: [Form],
      ages: [1, 2, 5, 3, 4],
    }
  },
  methods: {
    add() {
      this.children.push(Form)
    },
    deleteForm(indexForm) {
      console.log(indexForm)
      this.children.splice(indexForm, 1)
    },
  },
}
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
