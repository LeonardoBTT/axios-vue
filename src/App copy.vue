<script>
import { defineComponent, onMounted, ref } from "vue";
import axios from "axios";

export default defineComponent({
  setup() {
    const count = ref(0);
    const pokemons = ref([]);

    const fetchPokemons = () => {
      axios
        .get("https://pokeapi.co/api/v2/pokemon/ditto")
        .then((response) => {
          pokemons.value = response.data.sprites.back_default 
        });
    };

    onMounted(fetchPokemons);

    return {
      count,
      pokemons,
    };
  },
});
</script>

<template>
  <button @click="count++">{{ count }}</button>
  <img :src="pokemons">
</template>