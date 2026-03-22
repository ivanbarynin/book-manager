<template>
  <div class="book-card" :class="{ completed: book.completed }">
    <div>
      <h3>{{ book.title }}</h3>
      <p>{{ book.author }}</p>
      <span>{{ book.genre }}</span>
    </div>

    <div>
      <div v-if="book.completed">
        <span v-for="star in 5" :key="star" @click="$emit('rate', star)">
          {{ star <= book.rating ? '★' : '☆' }}
        </span>
      </div>

      <button @click="$emit('toggle')">
        {{ book.completed ? 'Прочитано' : 'Отметить' }}
      </button>

      <button @click="$emit('delete')">✕</button>
    </div>
  </div>
</template>

<script setup>
defineProps(['book'])
defineEmits(['toggle', 'delete', 'rate'])
</script>