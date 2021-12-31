<template>
  <Index />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Index from "./components/index.vue";

@Options({
  components: {
    Index,
  },
})
export default class App extends Vue {}
</script>
