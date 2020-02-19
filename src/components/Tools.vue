<template>
  <div class="hello">
    
    <h3>{{ title }}</h3>

    
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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
