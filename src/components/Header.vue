<template>
    <header class="nav">
      <i class="fas fa-bars"></i>
      <h2>{{ title }}</h2>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        title: String,
    },
}
</script>

<style scoped>
header {
  display: flex;
}

h2 {
  font-family: 'Open Sans';
  color: rgb(61, 60, 60);
  font-size: 20px;
  margin-top: 15px;
}

.nav {
  background: #e6cd69;
  margin-bottom: 25px;
  /* -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57); */
  /* -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57); */
  box-shadow: .5px 1px 5px rgba(70, 49, 49, 0.57);
  padding: 5px;
  border-radius: 5px;
}

.fas {
  color: rgb(61, 60, 60);
  font-size: 20px;
  margin: 20px;
  cursor: pointer;
  transition: transform .3s;
}
</style>
