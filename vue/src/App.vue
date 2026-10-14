<script setup>
  import { ref,reactive } from 'vue'

const message = ref('Hello World!')

let adminActivo = ref(false);

function admin() {
  adminActivo.value = !adminActivo.value;
}

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
  <button @click="admin">Admin</button>
  <div v-if="adminActivo">
    <h2>Administracion de gatos</h2>

    <form action="" method="post">
      <label for="nom" >Nom</label>
      <input type="text" v-model="data.gatos[data.catActive].name" name="nom" id="" placeholder="Nom de gat">
      <label for="imagen">Imagen</label>
      <input type="text" name="" id="" v-model="data.gatos[data.catActive].image">
      <label for="click">Clicks</label>
      <input type="number" name="click" id="" v-model="data.gatos[data.catActive].nclicks">
    </form>
  </div>

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
