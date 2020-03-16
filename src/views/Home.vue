<template>
  <div class="home">
    <MainSvg msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import MainSvg from "@/components/MainSvg.vue";

export default {
  name: "Home",
  components: {
    MainSvg
  }
};
</script>
