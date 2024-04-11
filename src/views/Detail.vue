<template>
  <div class="p-8">
    <h2 class="text-yellow-500 font-bold text-xl text-center mt-3">
      Mais detalhes sobre o pet
    </h2>
    <img
      :src="currentPet?.img"
      id="petimg"
      class="w-screen object-cover mt-5 object-top"
    />

    <div class="my-5 text-xl text-yellow-600 font-bold">
      <p class="text-center text-2xl text-blue-900 my-5">
        {{ currentPet?.name }}
      </p>
      <p>
        O pet {{ currentPet?.name }} é um animal muito querido, meigo e
        inteligente, tem {{ currentPet?.age }} anos, é da raça
        {{ currentPet?.breed }} e esta a procura de um lar com muito amor
        carinho e prosperidade. Para adotar esse simpatico animalzinho, é
        ncessário que preencha todos os requistos. Para saber mais basta entrar
        em contato com a nossa Administração via WhatsApp.
      </p>
    </div>
    <div class="text-right mt-2">
      <button
        class="px-1 py-1 text-white bg-yellow-500 hover:bg-yellow-400 m-2 rounded"
      >
        Adotar
      </button>
      <button
        @click="removeCurrentPet"
        class="px-1 py-1 text-white bg-red-500 hover:bg-red-400 m-2 rounded"
      >
        Remover
      </button>
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
  props: {
    id: { type: Number, required: true },
  },

  mounted() {
    this.getPets();
  },
  methods: {
    getPets() {
      this.pets = JSON.parse(localStorage.getItem("pets")) || [];
    },
    removeCurrentPet() {
      const currentId = this.id;
      const index = this.pets.findIndex((pet) => pet.id === currentId);
      if (index !== -1) {
        this.pets.splice(index, 1);
        localStorage.setItem("pets", JSON.stringify(this.pets));
        window.location.href = "/";
      }
    },
  },
  computed: {
    currentPet() {
      const currentId = this.id;
      return this.pets.find((pet) => pet.id === currentId);
    },
  },
};
</script>
