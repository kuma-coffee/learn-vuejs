<template>
  <div class="home">
    <h1>Home</h1>
    <!-- <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
    <button @click="age++">add 1 to age</button>
    <input type="text" v-model="name" /> -->
    <!-- <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update Ninja One</button>
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }} - {{ nameTwo }}</p>
    <button @click="updateNinjaTwo">Update Ninja Two</button> -->
    <input type="text" v-model="search" />
    <div v-for="name in mathcingNames" :key="name">{{ name }}</div>
    <button @click="handleClick">stop watching</button>
  </div>
</template>

<script>
import { computed, reactive, ref, watch, watchEffect } from "vue";

export default {
  name: "HomeView",
  // setup() {
  //   const p = ref();

  //   let name = "mario";
  //   let age = 30;

  //   const handleClick = () => {
  //     console.log(p, p.value);
  //     p.value.classList.add("test");
  //     p.value.textContent = "hello, ninjas";
  //   };

  //   return { name, age, handleClick, p };
  // },

  // setup() {
  //   const name = ref("mario");
  //   const age = ref(30);

  //   const handleClick = () => {
  //     name.value = "luigi";
  //     age.value = 40;
  //   };

  //   return { name, age, handleClick };
  // },

  // setup() {
  //   const ninjaOne = ref({ name: "mario", age: 30 });
  //   const ninjaTwo = reactive({ name: "nana", age: 50 });

  //   const nameOne = ref("mario");
  //   const nameTwo = reactive("nana");

  //   const updateNinjaOne = () => {
  //     ninjaOne.value.age = 40;
  //   };

  //   const updateNinjaTwo = () => {
  //     ninjaTwo.age = 45;
  //     // nameTwo = 'Lala'
  //   };

  //   return { ninjaOne, ninjaTwo, updateNinjaOne, updateNinjaTwo, nameTwo };
  // },
  setup() {
    const search = ref("");
    const names = ref(["mario", "lala", "nana", "john", "toad"]);

    const stopWatch = watch(search, () => {
      console.log("watch func ran");
    });

    const stopEffect = watchEffect(() => {
      console.log("watchEffect func ran", search.value);
    });

    const mathcingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value));
    });

    const handleClick = () => {
      stopWatch();
      stopEffect();
    };

    return { names, search, mathcingNames, handleClick };
  },
};
</script>
