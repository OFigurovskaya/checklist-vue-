<script>
import Task from './components/Task.vue';
export default {
  name: 'App',
  data() {
    return {
      message: '',
      tasks: [
        {
          id: 1,
          name: 'Сходить в магазин',
          done: false
        },
        {
          id: 2,
          name: 'Сделать чек-лист',
          done: false
        },
        {
          id: 3,
          name: 'Сделать второй проект',
          done: true
        },
      ]
    }
  },
  components: {
    Task,
  },
  methods: {
    add() {
      this.tasks.push({ id: this.message, name: this.message, done: false });
      this.message = '';
    },
    completed() {
      return this.tasks.filter(task => task.done);
    },
    unCompleted() {
      return this.tasks.filter(task => !task.done);
    },
    count() {
            return this.tasks.filter(task => !task.done).length;
        },
  },
  computed: {

  }
}
</script>

<template>
  <div class="wrapper" :class="{ main: true }">
    <h1>Список дел</h1>
    <div>
      <h3 :class="{bot1: true}">Осталось дел: {{ count() }}</h3>
      <Task :tasks="unCompleted()" />
    </div>
    <input v-model="message" @keyup.enter="add">
    <button @click="add" :class="{bot:true}">Добавить</button>
    <h3 :class="{bot1: true}">Выполненные дела:</h3>
    <Task :tasks="completed()" />
  </div>
</template>



<style>
.main {
  width: 80vw;
  margin: 0 auto;
  border: 2px solid black;
  padding: 5%;
  border-radius: 25px;
}

.delList {
  list-style: none;
}

.done {
  text-decoration: line-through;
}

.flex {
  display: flex;
}

.right {
  margin-left: 3%;
  text-align: right;
}

.check {
  width: 15px;
  margin-right: 1%;
}

.width {
  width: 200px;
}

.bot1 {
  margin-bottom: 2%;
}

.bot {
  margin-bottom: 3.5%;
}
</style>