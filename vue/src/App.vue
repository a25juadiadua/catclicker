<script setup>
  import { ref,reactive } from 'vue'

const message = ref('Hello World!')


let data = reactive({
        catActive: 0,
        ncats: 4,
        gatos: [
            { name: "Michifu", image: "../public/img/cat.jpg", nclicks: 0 },
            { name: "Minino", image: "../public/img/cat2.jpg", nclicks: 0 },
            { name: "Garfield", image: "../public/img/cat3.jpg", nclicks: 0 },
            { name: "Happy", image: "../public/img/cat4.jpeg", nclicks: 0 }
        ]
    });
    
function CatClicker(){
data.gatos[data.catActive].nclicks++; 
} 

function gatSeleccionat(index){
  data.catActive = index;
}

</script>

<template>
  <h1>Lista de gatos</h1>
  <ul>
    <li @click="gatSeleccionat(index)" v-for="actual,index in data.gatos">
      {{ actual.name }}
    </li>
  </ul>
  

  <div>
    <p>{{ data.gatos[data.catActive].name }}</p>
    <img @click="CatClicker" :src="data.gatos[data.catActive].image" alt="">
    <h1>{{ data.gatos[data.catActive].nclicks }}</h1>
  </div>

 
</template>

<style scoped></style>
