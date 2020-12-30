<template>
  <div>
    <h2>Skukurkite receptą</h2>
    <div>
      <div>Indegrientai</div>
      <input type="text" placeholder="produkto pavadinimas" />
      <input type="text" placeholder="kiekis" />
      <select>
        <option value="">Vienetai</option>
        <option value="">Gramai</option>
        <option value="">Mililitrai</option>
      </select>
      <button>add</button>
      <button>Delete</button>
    </div>
    <div>
      <label for="description">Recepto aprasymas</label>
      <textarea id="description"></textarea>
    </div>
  </div>
</template>
<script>
export default {
  name: 'AddRecept',
}
</script>
