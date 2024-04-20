<template>
  <div v-if="character" class="about">

    <div class=" grid md:grid-cols-1 lg:grid-cols-2 rounded-full">
      <div class="m-20">
        <img class="rounded-xl console-center" :src="character.image" alt="">
      </div>
      <div class="flex flex-col items-center m-20">
        <h1 class="text-3xl md:text-5xl text-center font-bold">{{ character.name }}</h1>
       <div class="flex">
        <Icon class=text-3xl icon="mdi:death" />
        <p class="text-2xl font-bold">Status: {{ character.status }}</p>
       </div>
       <div class="flex">
        <Icon class="text-3xl" icon="icons8:gender" />
        <p class="text-2xl  font-bold">Gender: {{ character.gender }}</p>
       </div>
       <div class="flex">
        <Icon class="text-3xl" icon="mdi:location" />
        <p class="text-2xl  font-bold">location: {{ character.location.name }}</p>
       </div>
       <div class="flex">
        <Icon class="text-3xl" icon="ph:planet-fill" />
        <p class="text-2xl  font-bold">Origin: {{ character.origin.name }}</p>
       </div>
        <div class="flex">
          <Icon class=text-3xl icon="material-symbols:person" /> 
          <p class="text-2xl  font-bold">Species: {{ character.species }}</p>
        </div>
      </div>  
      
      
    </div>
  </div>
</template>

<script setup>
  import { useRoute } from 'vue-router';
  import { onMounted, ref } from "vue";
  import { Icon } from '@iconify/vue';

  const route = useRoute()
  const characterId = route.params.id

  const character = ref(null)

  onMounted (async() => {
  try{
    const response = await fetch(`http://rickandmortyapi.com/api/character/${characterId}`);
    const data = await response.json()
    character.value = data
    console.log(data)
  }
  catch{
  }
  })
  

</script>
