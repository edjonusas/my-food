<template>
  <div class="preview-recept">
    <div class="recept-title">{{ recept.receptTitle }}</div>
    <div>
      <div class="img-block">
        <img
          src="https://images.unsplash.com/photo-1482049016688-2d3e1b311543?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=653&q=80"
          alt="recept-img"
        />
      </div>
      <div class="ingredient-block">
        <div v-for="(oneIngredient, index) in recept.ingredients" :key="index">
          <span>
            {{ oneIngredient.name + ' ' + oneIngredient.amount + ' ' + oneIngredient.unit }}
          </span>
          <button @click="deleteIngredient(index)">Ištrinti</button>
        </div>
      </div>
      <div class="description-block">
        <p>{{ recept.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    recept: {
      type: Object,
      required: true,
    },
  },
  methods: {
    /**
     *  emit delete ingredient index number
     */
    deleteIngredient(index) {
      this.$emit('delete-ingredient', index)
    },
  },
}
</script>
