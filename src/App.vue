<script setup>
import { reactive, ref } from 'vue';
import Progess from './components/Progess.vue';

// ref para primitivos: números, strings, booleanos
let count = ref(0);

// reactive para objetos
let courses = reactive([
  {
    title: 'JavaScript',
    done: true,
  },
  {
    title: 'Vue.js',
    done: false,
  },
  {
    title: 'Node.js',
    done: true,
  }
]);

let newCourse = {done: false};

function incrementar() {
  count.value++;
}

function addCourse() {
  courses.push(newCourse);
  newCourse = {done: false};
}

function completeCourse(title) {
  courses.forEach(course => {
    if (course.title === title) {
      course.done = !course.done;
    }
  });
}

</script>

<template>
  <div>
    <h1>Lista de cursos</h1>
    <ul>
      <li v-for="course in courses" :key="course.title">
        <p :class="course.done ? 'outline' : ''" @click="completeCourse(course.title)">{{ course.title }}</p>
      </li>
    </ul>

    <br>

    <input v-model="newCourse.title" type="text"/>
    <button @click="addCourse">Adicionar curso</button>

    <Progess :courses="courses" />

  </div>
</template>

<style scoped>
p.outline {
  text-decoration: line-through;
  color: gray;
}
</style>
