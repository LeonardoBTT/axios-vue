<script>
import { defineComponent, onMounted, ref } from "vue";
import axios from "axios";

export default defineComponent({
  data() {
    return {
      dados: ref([])
    }
  },
  methods: {
    getData() {
      axios.get("https://pokeapi.co/api/v2/pokemon/ditto").then((response) => {
        this.dados = response.data;
      });
    }
  },
  Mounted() {
    this.pegarDados();
  }
  });

</script>

<template>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3"
    crossorigin="anonymous"
  />
  
  <button @click="getData()">Pegar Dados</button>
  <button>Guardar Dados</button>
  <table class="table table-striped">
    <thead class="thead-dark">
      <tr>
        <th scope="col">Habilidade</th>
        <th scope="col">held_items</th>
        <th scope="col">game_indices</th>
      </tr>
    </thead>
    <tbody>
      <td>
        <tr v-for="(dado,index) in dados.abilities" :key="index" scope="row">
          {{ dado }}
        </tr>
      </td>
      <td>
        <tr v-for="(dado,index) in dados.held_items" :key="index" scope="row">
          {{ dado }}
        </tr>
      </td>
      <td>
        <tr v-for="(dado,index) in dados.game_indices" :key="index" scope="row">
          {{ dado }}
        </tr>
      </td>
    </tbody>
  </table>
</template>