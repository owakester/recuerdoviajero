<template>
<div>
    <img @click="pushStar(mystar)" class="h-4" :src="mystar" alt="">
    <p>{{mystar}}</p>
    

    <p>{{commentIds}}</p>
    <p>{{likes}}</p>

</div>
</template>


<script setup>

import {defineProps } from "vue";

defineProps({
 mystar: String,
  likes: Number,
  isPublished: Boolean,
  commentIds: Array,
 
});

/* let estrella=ref("images/starfull.png") */
const pushStar=()=>{
    
}



/*  let estrella = ref("images/starempty.png"); 
 */</script>