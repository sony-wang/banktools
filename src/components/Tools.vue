<template>
  <div class="wrapper">
    <div class="container">
    <h3>{{ title }}</h3>

    </div>
  </div>
</template>

<script>
export default {
  name: "Tools",
  props: {
    title:String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "~@/assets/css/style.scss";

</style>
