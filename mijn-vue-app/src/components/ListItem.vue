<template>
  <li>
    {{ text }}
    <input type="checkbox" :checked="completed" @change="changeCompleted">
    <input type="button" @click="deleteItemAdvanced" value="X" />
  </li>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  text: {
    type: String,
    required: true
  },
  index: {
    type: Number,
    required: true
  },
  completed: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['changeCompleted', 'deleteItemAdvanced'])

function changeCompleted() {
  emit('changeCompleted', props.index)
}

function deleteItemAdvanced() {
  emit('deleteItemAdvanced', props.index)
}
</script>
