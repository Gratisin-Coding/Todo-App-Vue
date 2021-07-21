<template>
  <li>
    <span>{{ todo }}</span>
    <button @click="onDelete">Delete Todo</button>
  </li>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TodoItem',
  props: {
    todo: String,
    onDelete: Function
  }
})
</script>
