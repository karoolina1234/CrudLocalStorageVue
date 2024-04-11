<template>
  <div class="mx-auto max-w-full">
    <img
      src="/public/img/cachorro-do-tiktok2-1280x720.jpg"
      alt=""
      class="w-screen object-cover h-96"
    />
    <h2 class="text-yellow-500 font-bold text-xl text-center mt-3">
      Listagem de animais
    </h2>
    <div
      class="grid sm:grid-cols-2 sm:grid-rows-2 md:grid-cols-5 md:grid-rows-5 p-5"
      v-if="pets.length > 0"
    >
      <div
        class="mx-2 text-blue-800 shadow-md text-center m-3 p-4"
        v-for="(pet, index) in pets"
        :key="index"
      >
        <img :src="pet.img" class="h-28 object-cover w-full" />
        <strong>{{ pet.name }}</strong> ({{ pet.species }})<br />
        Idade: {{ pet.age }}, Raça: {{ pet.breed }}<br />
        <div class="text-sm mt-2">
          <router-link
            class="bg-yellow-500 hover:bg-yellow-400 w-full text-white font-bold p-1 rounded focus:outline-none focus:shadow-outline"
            :to="{ name: 'detail', params: { id: pet.id } }"
          >
            Quero adotar
          </router-link>
        </div>
      </div>
    </div>
    <div class="text-center" v-else>
      <h2 class="text-xl font-bold text-blue-800 mt-7">
        Ops nenhum pet disponível no momento
      </h2>
      <img src="/public/img/bicho-de-estimacao.png" class="w-20 inline mt-4" />
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

  },
};
</script>
