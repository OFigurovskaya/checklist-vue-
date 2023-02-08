<script>
import Dislike from './Dislike.vue';
import Like from './Like.vue';
export default {
    name: 'Task',
    props: ['tasks'],
    data() {
        return {
            isEdit: false,
        }
    },
    components: {
    Like,
    Dislike,
    },
    methods: {
        edit(task) {
            task.isEdit = true;
        },
        save(task) {
            task.isEdit = false;
        },
        removeItem: function (index) {
            this.tasks.splice(index, 1);
        },
    },
    computed: {

    }
}
</script>

<template>
    <div v-for="(task, index) in tasks" :key="task.id" :class="{ delList: true, done: task.done, flex: true }">
        <template v-if="!task.isEdit">
            <input type="checkbox" v-model="task.done" :class="{ check: true }">
            {{ task.name }}
            <Like />
            <Dislike />
            <button @click="edit(task)">edit</button>
            <button @click="removeItem(index)">del</button>
        </template>
        <template v-else>
            <input v-model="task.name" @keyup.enter="save(task)">
            <button @click="save(task)">save</button>
        </template>
    </div>
    
</template>

<style>
.border {
    border: none;
    background-color: transparent;
}
</style>