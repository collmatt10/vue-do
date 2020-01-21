<template>
  <div>
    <b-container>
      <b-row>
        <b-col>
          <TodoList/>
        </b-col>
      </b-row>
    </b-container>

  </div>
</template>

<script>
import TodoList from  './components/TodoList';


export default {
  name: 'app',
  components: {
    TodoList
  }
}
</script>

<style>

</style>
