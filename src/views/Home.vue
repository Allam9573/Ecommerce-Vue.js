<template>
  <BasicLayout>
    <div class="container">
      <h2>Estamos en la Home</h2>
    </div>
  </BasicLayout>
</template>

<script>
// @ is an alias to /src
import BasicLayout from "../layout/BasicLayout.vue";
import Menu from "../components/Menu.vue";

export default {
  name: "Home",
  components: {
    BasicLayout,
  },
};
</script>
