<template>
  <div class="mt-2">
   
    <label for="">Pais nuevo </label>
    <input
      v-model="datoin"
      class="bg-gray-100 rounded text-gray-900"
      type="text"
      placeholder="Ingresa nombre del pais"
    />

    <label for="">imagen </label>
    <input
      v-model="imagein"
      class="bg-gray-100 rounded text-gray-900"
      type="text"
      placeholder="copia el link"
    />

    <button @click="sortCountries" class="bg-green-400 rounded mx-2 p-2">
      agregar
    </button>
    <h2 class="text-center text-3xl text-cyan-600 font-mono">
      Viajeros del Mes
    </h2>
    <div class="m-2 grid grid-cols-5 gap-4">
      <ul v-for="(pais, index) in paises" :key="pais.id">
        <li>
          <div class="shadow rounded border bg-gray-100 p-4 m-2 w-92 h-auto">
            <div class="grid grid-cols-3">
              <span class=""><img class="h-10 " :src="pais.bandera" alt="" /></span>
              <span class="bg-green-400 text-center text-2xl w-8 h-8 px-1 rounded m-1">{{ pais.score }}</span>
              <span class="text-green-800"> {{ pais.name }}</span>
            </div>
           
           
            <img class="w-96 rounded-t my-2" v-bind:src="pais.foto" />
            <div class="bg-gray-200 rounded-b">
              <div class="grid grid-cols-6 mx-16">
                <button
                @click="moreCount(index)"
                class="m-1 bg-green-700 text-gray-100 rounded  "
              >
                +
              </button>
                <img  v-if="pais.estrellas[pais.puntuacion[0]] == true"  @click="pointStart(index,pais.puntuacion[0])"  class="h-4 m-1"   :src="pais.starfull">
                <img  @click="pointStart(index,pais.puntuacion[0])"  class="h-4 m-1"  v-else  :src="pais.starempty" alt="">
                      
                    
                <img  v-if="pais.estrellas[pais.puntuacion[1]] == true"  @click="pointStart(index,pais.puntuacion[1])"  class="h-4 m-1"   :src="pais.starfull">
                <img  @click="pointStart(index,pais.puntuacion[1])"  class="h-4 m-1"  v-else  :src="pais.starempty" alt="">


                <img  v-if="pais.estrellas[pais.puntuacion[2]] == true"  @click="pointStart(index,pais.puntuacion[2])"  class="h-4 m-1"   :src="pais.starfull">
                <img  @click="pointStart(index,pais.puntuacion[2])"  class="h-4 m-1"  v-else  :src="pais.starempty" alt="">


                <img  v-if="pais.estrellas[pais.puntuacion[3]] == true"  @click="pointStart(index,pais.puntuacion[3])"  class="h-4 m-1"   :src="pais.starfull">
                <img  @click="pointStart(index,pais.puntuacion[3])"  class="h-4 m-1"  v-else  :src="pais.starempty" alt="">


                <img  v-if="pais.estrellas[pais.puntuacion[4]] == true"  @click="pointStart(index,pais.puntuacion[4])"  class="h-4 m-1"   :src="pais.starfull">
                <img  @click="pointStart(index,pais.puntuacion[4])"  class="h-4 m-1"  v-else  :src="pais.starempty" alt="">
              </div>

            
              <button @click="readMore(index)" class="bg-green-400 rounded p-1 m-1">Leer mas</button>
              <div class="p-2" v-if="pais.like==true" >
              
                <PostComment :comment="pais.note"></PostComment>
            </div>
            </div>

            <div>
              <!--                 <p v-for="puntuacion in paises.estrellas" :key="puntuacion.id">sd{{puntuacion}}</p>
 -->
            </div>

            <!--      <PointUser v-bind:comment-ids="[234, 266, 273]"></PointUser>

              <PointUser :likes="pais.puntuacion"></PointUser>
             -->

         
          </div>
        </li>
        <p>{{ name }}</p>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";
import PostComment from "./PostComment.vue";
/* import PointUser from "./pointUser.vue";
 */
defineProps(["phoneNumber", "emailAddress"]);

let datoin = ref("");
let imagein = ref("");
/* let points=[1,2,3,4,5]
 */ let paises = ref([
  {
    id: 1,
    bandera: "https://cdn-icons-png.flaticon.com/128/555/555617.png",
    name: "Rodrigo perez",
    note:"Amante de los viajes, apasionado por la naturaleza y la aventura",
    puntuacion: [0, 1, 2, 3, 4],
    score: 0,
    foto: "images/1.jpg",
    like: false,
    starempty: "images/starempty.png",
    starfull: "images/starfull.png",
    estrellas: [false, false, false, false, false],
  },
  {
    id: 2,
    bandera: "https://cdn-icons-png.flaticon.com/128/330/330430.png",
    name: "Cintia Espinoza",
    note:"Amante de los viajes, apasionado por la naturaleza y la aventura",
    puntuacion: [0, 1, 2, 3, 4],
    score: 0,
    foto: "images/2.jpg",
    like: false,
    starempty: "images/starempty.png",
    starfull: "images/starfull.png",
    estrellas: [false, false, false, false, false],
  },
  {
    id: 3,
    bandera: "https://cdn-icons-png.flaticon.com/128/630/630615.png",
    name: "Tatiana Rodriguez",
    note:"Amante de los viajes, apasionado por la naturaleza y la aventura",
    puntuacion: [0, 1, 2, 3, 4],
    score: 0,
    foto: "images/3.jpg",
    like: false,
    starempty: "images/starempty.png",
    starfull: "images/starfull.png",
    estrellas: [false, false, false, false, false],
  },
  {
    id: 4,
    bandera: "https://cdn-icons-png.flaticon.com/128/3371/3371965.png",
    name: "Santiago Sambrano",
    note:"Amante de los viajes, apasionado por la naturaleza y la aventura",
    puntuacion: [0, 1, 2, 3, 4],
    score: 0,
    foto: "images/4.jpg",
    like: false,
    starempty: "images/starempty.png",
    starfull: "images/starfull.png",
    estrellas: [false, false, false, false, false],
  },
  {
    id: 5,
    bandera: "https://cdn-icons-png.flaticon.com/128/555/555605.png",
    name: "Mijeong Kim",
    note:"Amante de los viajes, apasionado por la naturaleza y la aventura",
    puntuacion: [0, 1, 2, 3, 4],
    score: 0,
    foto: "images/5.jpg",
    like: false,
    starempty: "images/starempty.png",
    starfull: "images/starfull.png",
    estrellas: [false, false, false, false, false],
  },
]);

const sortCountries = () => {
  paises.value.push({
    id: 5,
    nombre: datoin.value,
    puntuacion: [0, 1, 2, 3, 4],
    score: 0,
    foto: imagein.value,
    like: false,
    starempty: "images/starempty.png",
    starfull: "images/starfull.png",
    estrellas: [false, false, false, false, false],
  });
};

const moreCount = (points) => {
  paises.value[points].score++;

setTimeout(() => {

  console.log(paises.value.sort((a, b) => a.score - b.score));
}, 2000);



};

const pointStart = (valor, numstar) => {
  if (paises.value[valor].estrellas[numstar] == false) {
    paises.value[valor].estrellas[numstar] = !false;

    for (let i = 0; i < numstar; i++) {

      let seleccion = (paises.value[valor].estrellas[i] = true);
      console.log(seleccion);

    }
  } else {
    paises.value[valor].estrellas[numstar] = false;
    for (let i = 0; i < paises.value.length; i++) {
 

      let seleccion = (paises.value[valor].estrellas[i] = false);
      console.log(seleccion);
    }
  }
};

//Despliega comentarios
const readMore = (valor) => {
  paises.value[valor].like=!paises.value[valor].like
};


</script>

<style></style>
