<template>
  <div class="container">
    <div class="habit">
      <!-- title -->
      <div class="title">
        <h1>Habit List</h1>
      </div>
      <!-- form -->
      <div class="form">
        <input type="text" placeholder="New Habit" v-model="newHabit" @keyup.enter.exact="addHabit()" />
        <button @click="addHabit()"><i class="fas fa-plus"></i></button>
      </div>
      <!-- habit lists -->
        <ul>
          <div class="habitItems">
              <habit-item v-bind:habit="habit" v-for="(habit, index) in habits" :key="habit.id" @delete="deleteHabit(index)"></habit-item>
          </div>
        </ul>
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
import HabitItem from './Habit-item';

export default {
  name: "Habit",
  props:['habits'],
  components:{
    HabitItem
  }
  ,
  data() {
    return {
      newHabit: ""
    }
  },
  computed:{
    incomplete(){
      return this.habits.filter(this.inProgress).length;
    }
  },
  methods: {
    addHabit(){
      if(this.newHabit){
        this.habits.push(
          {
            title: this.newHabit,
            completed: false
          }
        );
        this.newHabit = "";
      }
    },
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
    },
    deleteHabit(index){
      this.habits.splice(index, 1);
    },
  },
};
</script>
