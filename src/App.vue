<template>
  <div id="app">
    <BaseLayout>
      
      <template #header>
        <h1>Jedi</h1>
      </template>

      
      <template #main>
        <CardRender
          v-for="(item, index) in database"
          :key="index"
          :name="item.name"
          :department="item.deparment"
          :salary="item.salary"
          :position="index"
          v-on:deleteItem="deleteCard"
        />
      </template>

      
      <template #footer>
        <p>May the force be with you</p>
      </template>
    </BaseLayout>
  </div>
</template>

<script setup>
import { ref } from "vue";
import CardRender from "./components/CardRender.vue";
import BaseLayout from "./components/BaseLayout.vue";

let database = ref([
  {
    name: "Anakin",
    deparment: "Jedi",
    salary: 30000
  },
  {
    name: "Obi-Wan",
    deparment: "Jedi-Master",
    salary: 72000
  },
  {
    name: "Yoda",
    deparment: "Jedi-Master-Grandmaster",
    salary: 125000
  }
]);

function deleteCard(position) {
  console.log("This card have been pressed:", database.value[position])
  database.value.splice(position, 1);

}

</script>


<style scoped></style>
