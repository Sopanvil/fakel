<script lang="ts" setup>
import Home from '@/views/Home.vue'
import Header from "./components/widgets/Header.vue";
import Container from "@/components/shared/Container.vue";

import cards from "@/storage/cards.json";
import projects from "@/storage/projects.json";
import stages from "@/storage/stages.json";

  let cardsData = cards
  let projectsData = projects
  let stagesData = stages

  
  
</script>

<template>
  <Container>
    <Header />
    <Home :cards="cardsData" :projects="projectsData" :stages="stagesData"/>
  </Container>
</template>

<style lang="scss" scoped></style>
