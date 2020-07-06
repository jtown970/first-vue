<template>
<!-- $ means that you're using a Vue instance property or an Vue instance method. -->
  <li>
    <button 
    v-if="!isEditing"
    :class="{completed}"
    
    @click="$emit('on-toggle')"
    >{{todoString}}</button>
    <form v-else @submit.prevent="endEditing()">
      <input @blur="startEditing()" v-model="newTodoString" type="text"/>
    </form>
    <button @click="startEditing()" >Edit</button>
    <button @click="$emit('on-delete')" >Delete</button>
  </li>
</template>

<script>
export default{
  props:{
    todoString: String,
    completed: Boolean
  },
  // note must have a return in there
  data(){
    return{
      isEditing: false,
      newTodoString: ""
    }
  },
  methods: {
    startEditing(){
      if (!this.isEditing){
        this.newTodoString = this.todoString;
        this.isEditing = true
      } else {
        this.endEditing();
      }
    },
    endEditing(){
      this.isEditing = false;
      this.$emit('on-edit', this.newTodoString)
    }
  }
}

</script>

<style scoped>
/* note that scoped means it keeps the styles to this component */
.completed {
  text-decoration: line-through;
}
</style>>

