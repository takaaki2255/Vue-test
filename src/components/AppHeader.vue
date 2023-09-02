<script setup>
defineProps(["color"]);
</script>

<template>
  <header>
    <h1 v-bind:style="{ color: color }"><slot>No Title</slot></h1>
  </header>
</template>
