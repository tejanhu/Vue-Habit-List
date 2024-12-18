<template>
         <li>
            <button v-on:click="$emit('complete')" v-bind:class="className"><i class="far fa-circle"></i>{{habit.title}}</button>
            <button v-on:click="$emit('delete')"><i class="far fa-trash-alt"></i></button>
        </li>
</template>

<script>

export default ({
    name: 'HabitItem',
    props: ['habit'],
    computed: {
        className() {
            let classes = ['toggle'];
            if(this.habit.completed){
                classes.push("toggle-completed");
            }
            return classes;
        }
    },
})
</script>
