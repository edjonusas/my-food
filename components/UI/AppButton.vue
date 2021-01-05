<template>
  <button @click="$emit('clicked')"><slot /></button>
</template>

<script>
export default {
  name: 'AppButton',
}
</script>

<style>
button {
  outline-color: #5eba7d;
  font-weight: 600;
  font-size: 0.9rem;
  color: #fff;
  border: 2px solid #5eba7d;
  background-color: #5eba7d;
  border-radius: 4px;
  margin: 0.5rem 0;
  padding: 0.7rem 0.8rem;
  box-sizing: border-box;
  width: 100%;
}
</style>
