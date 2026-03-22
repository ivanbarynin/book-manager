<template>
  <div>
    <input v-model="searchQuery" placeholder="Поиск..." />

    <button @click="$emit('update:filter', 'all')">Все</button>
    <button @click="$emit('update:filter', 'read')">Прочитанные</button>
    <button @click="$emit('update:filter', 'unread')">Непрочитанные</button>

    <p>
      Всего: {{ total }} |
      Прочитано: {{ completed }} |
      Осталось: {{ total - completed }}
    </p>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps(['filter', 'books'])
defineEmits(['update:filter'])

const searchQuery = defineModel('searchQuery')

const total = computed(() => props.books.length)
const completed = computed(() =>
  props.books.filter(b => b.completed).length
)
</script>