<script>
export default {
    name: 'Dislike',
    data() {
        return {
            counter: 0,
        }
    },
    methods: {
        increment: function() {
            this.counter++;
        }
    },
    computed: {

    }
}
</script>

<template>
    <button type="button" :class="{border: true}" @click="increment">&#128078; {{this.counter}}</button>
</template>