<<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>

    <todo
      v-on:complete-todo="completeTodo"
      v-on:delete-todo="deleteTodo"
      v-for="todo in todos"
      v-bind:todo="todo">
    </todo>
  </div>
</template>

<script type="text/javascript">
import Todo from './Todo'

export default {
  components: {
    Todo
  },
  props: ['todos'],
  methods: {
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
    },
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 10)
    }
  }
}
</script>

<style>

</style>
