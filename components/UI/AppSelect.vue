<template>
  <div>
    <select @input="$emit('select', $event.target.value)">
      <option v-for="(option, index) in options" :key="index" :value="option.value">
        {{ option.name }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'AppSelect',
  props: {
    options: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style>
select {
  outline-color: #5eba7d;
  font-size: 0.9rem;
  border: 2px solid #d3d3d3;
  border-radius: 4px;
  margin: 0.2rem 0;
  padding: 0.7rem 0.8rem;
  box-sizing: border-box;
  width: 100%;
}
</style>
