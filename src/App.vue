<template>
  <div>
    <DynamicLink :animalComponent="selectedAnimal" :key="selectedAnimal" /> 
    <!-- key is for force update DynamicLink component -->
    <select v-model="selectedAnimal">
      <option value="" selected="selected"> </option>
      <option value="birds">birds</option>
      <option value="cats">cats</option>
      <option value="dogs">dogs</option>
    </select>
  </div>
</template>

<script>
import DynamicLink from "./components/DynamicLink";

export default {
  name: "App",
  data() {
    return {
      selectedAnimal: 'default',
    }
  },
  components: {
    DynamicLink,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
select {
  font-size: 20px;
}
</style>
