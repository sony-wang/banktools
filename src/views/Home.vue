<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <Tools title="下载工具站"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Tools from "@/components/Tools.vue";

export default {
  name: "Home",
  components: {
    Tools
  }
};
</script>
