<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      cocktails: [],
      baseUrl: 'http://127.0.0.1:8000/',
      apiUrls: {
        cocktails: 'api/cocktails'
      },
    }
  },
  methods: {
    getCocktails() {
      axios.get(this.baseUrl + this.apiUrls.cocktails).then(response => {
        this.cocktails = response.data.results;
        console.log(response)
      }).catch(error => {
        console.log(error);
      });
    }
  },
  created() {
    this.getCocktails();
  },
  components: {

  },
}
</script>

<template>

<div class="row mt-5">
  <div class="card col col-md-6 g-5" v-for="cocktail in cocktails">
    <div class="card-body">
      <h5 class="card-title">{{ cocktail.nome_cocktail }}</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">{{ cocktail.categoria_cocktail }}</h6>
      <p class="card-text">Ingrediente principale: {{ cocktail.ingrediente_principale }}</p>
      <p class="card-text">decorazione: {{ cocktail.decorazione }}</p>
      <span>{{ cocktail.alcolico === 1 ? "si, è alcolico" : "no, non è alcolico" }}</span>
    </div>
  </div>
  </div>

</template>

<style scoped lang="scss">
  .card{
    width: calc((100% / 2) - 20px);
    margin: 10px;
  }
</style>