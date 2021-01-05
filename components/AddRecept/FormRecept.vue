<template>
  <div class="recept-form">
    <h2>Sukurkite receptą</h2>
    <div>
      <div>
        <label for="recept-title">Recepto pavadinimas</label>
        <input id="recept-title" v-model="recept.receptTitle" type="text" />
      </div>
      <div class="ingredient-form">
        <div>Ingredientai</div>
        <input v-model="ingredient.name" type="text" placeholder="produkto pavadinimas" />
        <input v-model="ingredient.amount" type="text" placeholder="kiekis" />
        <select v-model="ingredient.unit">
          <option disabled selected>Vienetai</option>
          <option value="vnt.">Vienetai</option>
          <option value="gr.">Gramai</option>
          <option value="ml.">Mililitrai</option>
          <option value="arbatiniai šaukštai">Arbatiniai šaukštai</option>
          <option value="valgomieji šaukštai">Valgomieji šaukštai</option>
          <option>stiklinės</option>
        </select>
        <button @click="addIngredient">Pridėti</button>
        <span v-if="ingredientErrorMessage !== ''"> {{ ingredientErrorMessage }}</span>
      </div>
    </div>
    <div>
      <label for="description">Recepto aprasymas</label>
      <textarea id="description" v-model="recept.description"></textarea>
    </div>
    <div>
      <label for="img-url">Recepto nuotraukos url</label>
      <input id="img-url" type="text" />
    </div>
    <slot></slot>
    <button @click="saveRecept">Issaugoti</button>
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
  data() {
    return {
      ingredient: {
        name: '',
        amount: null,
        unit: '',
      },
      ingredientErrorMessage: '',
      ReceptFormErrorMessage: '',
    }
  },
  methods: {
    /**
     *  emit input values
     */
    addIngredient() {
      if (
        this.ingredient.name !== '' &&
        this.ingredient.amount !== null &&
        this.ingredient.unit !== ''
      ) {
        if (Number.isInteger(Number(this.ingredient.amount))) {
          this.$emit('add-ingredient', this.ingredient)
          // reset ingredient values
          this.ingredient.name = ''
          this.ingredient.amount = null
          this.ingredient.unit = ''
          this.ingredientErrorMessage = ''
        } else {
          this.ingredientErrorMessage = ' Laukelyje kiekis įveskite skaičių'
        }
      } else {
        this.ingredientErrorMessage = 'Užpildykite visus laukelius'
      }
    },
    /**
     *  emit form
     */
    saveRecept() {
      if (this.recept.receptTitle !== '') {
        console.log('veikia seivas')
      }
      // this.$emit('save-recept', this.recept)
    },
  },
}
</script>
