<template>
  <div>
    <Filters @filter="applyFilters" />
    <div class="character-list">
      <CharacterCard v-for="character in characters" :key="character.id" :character="character" />
    </div>
    <Pagination @change-page="fetchCharacters" />
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
import { useStore } from 'vuex';
import Filters from '../components/CharacterFilters.vue';
import CharacterCard from '../components/CharacterCard.vue';
import Pagination from '../components/CharacterPagination.vue';

export default {
  components: { Filters, CharacterCard, Pagination },
  setup() {
    const store = useStore();
    const characters = ref([]);

    const fetchCharacters = async (page = 1) => {
      await store.dispatch('fetchCharacters', { page });
      characters.value = store.state.characters;
    };

    const applyFilters = () => {
      // Logic for applying filters based on species or name
    };

    onMounted(() => {
      fetchCharacters();
    });

    return { characters, fetchCharacters, applyFilters };
  },
};
</script>
