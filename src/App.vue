<template>
  <div class="header-wrapper">
    <h1 class="logo">Hello {{name}}</h1>
    <button @click="showAlert">Click Me</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      name : "James"
    }
  },
  methods : {
    showAlert(e) {
      alert("Hello " + this.name);
    }
  }
}
</script>

<style lang="scss">
.header-wrapper{
  text-align: center;
  color:red;
}
</style>
