<template>
  <div id="app">
    <habit v-bind:habits="habits"></habit>
  </div>
</template>

<script>
import Habit from "./components/Habit";

export default {
  name: "App",
  components: {
    Habit,
  },
  data() {
    return {
      habits: [
        {
          id: 1,
          title: "Code for 10 mins",
          completed: false,
        },
        {
          id: 2,
          title: "Learn new vocabulary for 20 mins",
          completed: false,
        },
        {
          id: 3,
          title: "Exercise for 15 mins",
          completed: true,
        },
        {
          id: 4,
          title: "Eat one of your 5 a day",
          completed: false,
        },
        {
          id: 5,
          title: "Vacuum the house once a week",
          completed: true,
        },
      ],
    };
  },
};
</script>