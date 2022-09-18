<template>
  <div>
   {{comment}}
  </div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  comment: String,
 
});
</script>
