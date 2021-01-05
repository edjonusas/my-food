<template>
  <div class="recept-form">
    <h2>Recepto įkėlimas</h2>
    <app-input id="recept-title" label="Recepto pavadinimas" @input="inputTitle" />
    <app-input
      id="description"
      :textarea="true"
      label="Recepto aprasymas"
      @input="inputDescription"
    />
    <app-input id="img-url" label="Recepto nuotraukos url" @input="inputImgUrl" />
    <div class="ingredient-form">
      <app-input
        id="ingredient-name"
        label="Ingredientai"
        place-holder="ingrediento pavadinimas"
        @input="inputIngredientName"
      />
      <app-input place-holder="kiekis" @input="inputIngredientAmount" />
      <app-select :options="unitOptions" @select="selectedUnit" />
      <app-button @clicked="addIngredient">Pridėti</app-button>
      <span v-if="ingredientErrorMessage !== ''"> {{ ingredientErrorMessage }}</span>
      <slot />
    </div>
    <app-button @clicked="saveRecept">Issaugoti</app-button>
  </div>
</template>

<script>
import AppButton from '../UI/AppButton.vue'
import AppInput from '../UI/AppInput.vue'
import AppSelect from '../UI/AppSelect.vue'
export default {
  components: { AppInput, AppSelect, AppButton },
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
      unitOptions: [
        { value: 'vnt.', name: 'Vienetai' },
        { value: 'gr.', name: 'Gramai' },
        { value: 'ml.', name: 'Mililitrai' },
        { value: 'arbatiniai šaukštai', name: 'Arbatiniai šaukštai' },
        { value: 'valgomieji šaukštai', name: 'Valgomieji šaukštai' },
        { value: 'stiklinės', name: 'Stiklinės' },
      ],
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
    inputTitle(input) {
      this.recept.receptTitle = input
    },
    inputDescription(input) {
      this.recept.description = input
    },
    inputImgUrl(input) {
      this.recept.imageUrl = input
    },
    inputIngredientName(input) {
      this.ingredient.name = input
    },
    inputIngredientAmount(input) {
      this.ingredient.amount = input
    },
    selectedUnit(select) {
      this.ingredient.unit = select
    },
  },
}
</script>

<style scoped>
h2 {
  text-align: center;
}

.recept-form {
  margin: 0 10px;
}
</style>
