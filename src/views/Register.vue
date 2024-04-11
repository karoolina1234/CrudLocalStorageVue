<template>
  <div class="contentForm mt-6">
    <h1 class="text-yellow-500 font-bold mb-4 text-2xl">Cadastro de pets</h1>

    <form
      @submit.prevent="savePet"
      class="max-w-xl mx-auto bg-blue-900 shadow-md rounded px-8 pt-6 pb-8 mb-4 text-white"
    >
      <div class="mb-1">
        <label for="name" class="block text-sm font-bold mb-1">Nome:</label>
        <input
          type="text"
          id="name"
          v-model="pet.name"
          required
          class="shadow appearance-none border rounded w-full py-2 px-3 leading-tight focus:outline-none focus:shadow-outline"
        />
      </div>

      <div class="mb-1">
        <label for="age" class="block text-sm font-bold mb-1">Idade:</label>
        <input
          type="number"
          id="age"
          v-model="pet.age"
          required
          class="shadow appearance-none border rounded w-full py-2 px-3 leading-tight focus:outline-none focus:shadow-outline"
        />
      </div>

      <div class="mb-1">
        <label for="breed" class="block text-sm font-bold mb-1">Raça:</label>
        <input
          type="text"
          id="breed"
          v-model="pet.breed"
          required
          class="shadow appearance-none border rounded w-full py-2 px-3 leading-tight focus:outline-none focus:shadow-outline"
        />
      </div>

      <div class="mb-1">
        <label for="species" class="block text-sm font-bold mb-1"
          >Espécie:</label
        >
        <input
          type="text"
          id="species"
          v-model="pet.species"
          required
          class="shadow appearance-none border rounded w-full py-2 px-3leading-tight focus:outline-none focus:shadow-outline"
        />
      </div>

      <div class="mt-5 text-right">
        <button
          type="submit"
          class="bg-green-500 hover:bg-green-800 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
        >
          Adicionar
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pet: {
        name: "",
        age: 0,
        breed: "",
        species: "",
      },
    };
  },
  methods: {
    savePet() {
      let pets = JSON.parse(localStorage.getItem("pets")) || [];
      pets.push(this.pet);
      localStorage.setItem("pets", JSON.stringify(pets));
      this.pet = { name: "", age: 0, breed: "", species: "" };
    },
  },
};
</script>
