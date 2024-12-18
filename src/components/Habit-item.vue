<template>
         <li>
            <button><i class="far fa-circle"></i>{{habit.title}}</button>
            <button v-on:click="$emit('delete')"><i class="far fa-trash-alt"></i></button>
        </li>
</template>

<script>

export default ({
    name: 'HabitItem',
    props: ['habit'],
})
</script>
