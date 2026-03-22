<template>
  <form @submit.prevent="handleSubmit">
    <h2>Добавить книгу</h2>

    <input v-model="formData.title" placeholder="Название" required />
    <input v-model="formData.author" placeholder="Автор" required />

    <select v-model="formData.genre" required>
      <option value="">Жанр</option>
      <option>Роман</option>
      <option>Фантастика</option>
      <option>Детектив</option>
    </select>

    <button type="submit">Добавить</button>
  </form>
</template>

<script setup>
import { reactive } from 'vue'

const emit = defineEmits(['add-book'])

const formData = reactive({
  title: '',
  author: '',
  genre: ''
})

const handleSubmit = () => {
  emit('add-book', { ...formData })

  formData.title = ''
  formData.author = ''
  formData.genre = ''
}
</script>