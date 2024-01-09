<script>
import WhatsAppCardComp from "./components/WhatsAppCardComp.vue";
export default {
  name: "App",
  components: {
    WhatsAppCardComp,
  },
};
</script>

<template>
  <div class="container-app">
    <WhatsAppCardComp />
  </div>
</template>

<style lang="scss">
@use "./styles/variables" as *;

.container-app {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient($whatsapp-green 13%, $main-bg 13%);
  font-family: Arial, Helvetica, sans-serif;
}
</style>
