<template>
  <div class="mx-auto max-w-full">
    <img
      src="/public/img/cachorro-do-tiktok2-1280x720.jpg"
      alt=""
      class="w-screen object-cover h-96"
    />
    <h2 class="text-yellow-500 font-bold text-xl text-center">
      Listagem de animais
    </h2>
    <div class="grid grid-cols-5 grid-rows-5 p-5">
      <div
        class="mx-2 text-blue-800 shadow-md text-center m-3 p-4"
        v-for="(pet, index) in pets"
        :key="index"
      >
        <img :src="pet.img" class="h-28 object-cover w-full" />
        <strong>{{ pet.name }}</strong> ({{ pet.species }})<br />
        Idade: {{ pet.age }}, Raça: {{ pet.breed }}<br />
        <div class="text-sm mt-2">
          <button
            class="bg-yellow-500 hover:bg-yellow-400 w-full text-white font-bold p-1 rounded focus:outline-none focus:shadow-outline"
            @click="removePet(index)"
          >
            Quero adotar
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
