<template>
  <div class="mt-5 mx-auto max-w-xl">
    <h2 class="text-green-800 font-bold text-xl text-center">
      Pets Disponíveis para Adoção
    </h2>
    <div class="grid grid-cols-2 grid-rows-2">
      <div
        class="mx-2 bg-purple-500 text-white rounded-md text-center m-3"
        v-for="(pet, index) in pets"
        :key="index"
      >
        <strong>{{ pet.name }}</strong> ({{ pet.species }})<br />
        Idade: {{ pet.age }}, Raça: {{ pet.breed }}<br />
        <div class="text-right m-2">
          <button
            class="bg-red-600 hover:bg-red-400 text-white font-bold py-0.5 px-1 rounded focus:outline-none focus:shadow-outline"
            @click="removePet(index)"
          >
            X
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pets: [],
    };
  },
  mounted() {
    this.getPets();
  },
  methods: {
    getPets() {
      this.pets = JSON.parse(localStorage.getItem("pets")) || [];
    },
    removePet(index) {
      this.pets.splice(index, 1);
      localStorage.setItem("pets", JSON.stringify(this.pets));
    },
  },
};
</script>
