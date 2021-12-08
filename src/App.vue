<template>
  <div id="app">
    <v-sheet height="70" width="230" rounded color="white" outlined>
      <v-avatar />
    </v-sheet>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import VAvatar from "@/components/VAvatar/VAvatar.vue";
import VSheet from "@/components/VSheet/VSheet.vue";

@Component({
  components: {
    VAvatar,
    VSheet,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
