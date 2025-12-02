<script setup>
import { computed } from 'vue';

const props = defineProps(['courses']);

const completedCourses = computed(() => {
  return props.courses.filter(course => course.done).length;
});

</script>

<template>
  <div>
    <h1>{{ `${completedCourses} cursos completos de um total de ${courses.length}` }}</h1>
  </div>
</template>