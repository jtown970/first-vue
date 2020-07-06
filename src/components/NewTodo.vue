<template>
<form  @submit.prevent="addTodo()">
 <input v-model="newTodo" placeholder="Enter todo" type="text" />
</form>
  
</template>

<script>
export default {
  data(){
    return {
      newTodo: ""
    }
  },
  methods: {
    addTodo(){
      // note emit is used for sending custom events
      if (this.newTodo.length > 1){
        this.$emit("on-addtodo", this.newTodo)
      }
      this.newTodo = "";
    }
  }
}

</script>

<style scoped>

</style>