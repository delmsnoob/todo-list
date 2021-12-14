<template>
  <button @click="onClick()">
    {{ text }}
  </button>
</template>

<script>
export default {
  name:'ToggleAddTodo',
  props: {
    text: String,
  },
  methods: {
    onClick() {
      this.$emit('toggle-click')
    }
  }
}
</script>