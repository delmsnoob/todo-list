<template>
    <header class="nav-bar">
        <i class="fas fa-bars"></i>
        <h2> {{ title }} </h2>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        title: String,
    }
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: center;
}

h2 {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #fff;
}

.nav-bar {
  background: #79d9a1;
  height: 60px;
  margin-bottom: 25px;
  /* -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57); */
  /* -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57); */
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.57);
}

.fas {
  color: #fff;
  font-size: 20px;
  margin: 20px;
}
</style>
