<template>
  <div class="container">
    <div class="habit">
      <!-- title -->
      <div class="title">
        <h1>To Do List</h1>
      </div>
      <!-- form -->
      <div class="form">
        <input type="text" placeholder="New Habit" />
        <button><i class="fas fa-plus"></i></button>
      </div>
      <!-- habit lists -->
      <div class="habitItems">
        <ul>
          <li v-for="habit in habits" :key="habit.id">
            <button><i class="far fa-circle"></i>{{habit.title}}</button>
            <button><i class="far fa-trash-alt"></i></button>
          </li>
        </ul>
      </div>
      <!-- buttons -->
      <div class="clearBtns">
        <button v-on:click="clearCompleted()">Clear completed</button>
        <button @click="clearAll()">Clear all</button>
      </div>
      <!-- pending habit -->
      <div class="pendingHabits">
        <span>Pending Habits: {{incomplete}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Habit",
  props:['habits'],
  computed:{
    incomplete(){
      return this.habits.filter(this.inProgress).length;
    }
  },
  methods: {
    inProgress(habit){
      return !this.isCompleted(habit);
    },
    isCompleted(habit){
      return habit.completed;
    },
    clearCompleted(){
      this.habits = this.habits.filter(this.inProgress);
    },
    clearAll() {
      this.habits = [];
    }
  },
};
</script>
