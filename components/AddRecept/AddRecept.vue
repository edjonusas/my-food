<template>
  <div>
    <form-recept :recept="recept" @add-ingredient="addIngredient">
      <preview-recept :recept="recept" @delete-ingredient="deleteIngredient" />
    </form-recept>
  </div>
</template>
<script>
import FormRecept from './FormRecept.vue'
import PreviewRecept from './PreviewRecept.vue'

export default {
  name: 'AddRecept',
  components: { PreviewRecept, FormRecept },
  data() {
    return {
      recept: {
        receptTitle: '',
        ingredients: [],
        description: '',
        imageUrl: '',
      },
    }
  },
  methods: {
    /**
     *  add ingredient object to recept ingredients array
     */
    addIngredient(ingredient) {
      this.recept.ingredients.push({
        name: ingredient.name,
        amount: ingredient.amount,
        unit: ingredient.unit,
      })
    },
    /**
     *  delete ingredient object from recept ingredients array
     */
    deleteIngredient(index) {
      this.recept.ingredients.splice(index, 1)
    },
  },
}
</script>
