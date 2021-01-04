<template>
  <div>
    <div class="recept-form">
      <h2>Skukurkite receptą</h2>
      <div>
        <div>
          <label for="recept-title">Recepto pavadinimas</label>
          <input id="recept-title" v-model="recept.receptTitle" type="text" />
        </div>
        <div>Indegrientai</div>
        <div>
          <input type="text" placeholder="produkto pavadinimas" />
          <input type="text" placeholder="kiekis" />
          <select>
            <option>Vienetai</option>
            <option>Gramai</option>
            <option>Mililitrai</option>
            <option>Arbatiniai šaukštai</option>
            <option>Valgomieji šaukštai</option>
            <option>stiklinės</option>
          </select>
        </div>

        <button>Pridėti</button>
      </div>
      <div>
        <label for="description">Recepto aprasymas</label>
        <textarea id="description"></textarea>
      </div>
      <div>
        <label for="img-url">Recepto nuotraukos url</label>
        <input id="img-url" type="text" />
      </div>
    </div>
    <div class="recept-preview">
      <div class="recept-title-preview">{{ recept.receptTitle }}</div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'AddRecept',
  data() {
    return {
      recept: {
        receptTitle: '',
        ingredients: [],
        description: '',
        imageUrl: '',
      },
      ingredient: {
        name: '',
        amount: '',
        unit: '',
      },
    }
  },
}
</script>
