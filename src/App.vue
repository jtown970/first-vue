<template>
<!-- note just like react need to wrap in one div just give one component -->
  <div>
    <h1>hello from a vue</h1>
    <TodoList/>
  </div>
</template>

<script>
import TodoList from "./components/TodoList"
export default {
  name: "App",
  components: {
    TodoList
  }
}
</script>

<style>
body{
  background-color: rgb(66,66,66);
  color: aliceblue;
}

</style>