<template>
<div>
  <h1>Dynamic Component Template</h1>
  <component :is="myComponent" />
</div>
</template>

<script>
import { shallowRef, defineAsyncComponent } from 'vue'
export default {
  props: {
    animalComponent: String,
  },

  data() {
    return {
      myComponent: "",
    };
  },

  computed: {
    loader() {
      return () => import(`../templates/${this.animalComponent}`)
    },
  },

  created() {
    // shallowRef solve this issue: [Vue warn]: Vue received a Component which was made a reactive object. 
    // defineAsyncComponent solve this issue: [Vue warn]: Invalid VNode type: undefined (undefined)
    this.myComponent = shallowRef(defineAsyncComponent(() => this.loader()));
  },
};
</script>
