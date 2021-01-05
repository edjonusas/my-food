<template>
  <div class="app-input">
    <label v-if="label !== ''" :for="id">{{ label }}</label>
    <input
      v-if="textarea === false"
      :id="id"
      :type="inputType"
      :placeholder="placeHolder"
      @input="$emit('input', $event.target.value)"
    />
    <textarea
      v-if="textarea === true"
      :id="id"
      :placeholder="placeHolder"
      @input="$emit('input', $event.target.value)"
    ></textarea>
  </div>
</template>

<script>
export default {
  name: 'AppInput',
  props: {
    label: {
      default: '',
      type: String,
    },
    placeHolder: {
      default: '',
      type: String,
    },
    id: {
      default: '',
      type: String,
    },
    inputType: {
      default: 'text',
      type: String,
    },
    textarea: {
      default: false,
      type: Boolean,
    },
  },
}
</script>

<style scoped>
.app-input {
  display: flex;
  flex-direction: column;
}

label {
  font-weight: 600;
  font-size: 0.9rem;
  margin: 0.9rem 0.1rem 0.5rem;
  margin-left: 0.1rem;
}

input,
textarea {
  outline-color: #5eba7d;
  font-size: 0.9rem;
  border: 2px solid #d3d3d3;
  border-radius: 4px;
  margin: 0.2rem 0;
  padding: 0.7rem 0.8rem;
  box-sizing: border-box;
  width: 100%;
}

textarea {
  height: 10rem;
  resize: none;
}
</style>
