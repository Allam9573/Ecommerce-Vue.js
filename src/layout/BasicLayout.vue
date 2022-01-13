<template>
  <div>
    <Menu />
    <slot />
  </div>
</template>

<script>
import Menu from "../components/Menu.vue";
export default {
  name: "BasicLayout",
  components: {
    Menu,
  },
};
</script>

<style>
</style>