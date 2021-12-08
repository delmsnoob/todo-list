<template>
  <header>
    <i class="fas fa-bars"></i>    
    <div class="nav-title">
      <h2>{{ title }}</h2>
    </div>
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
h2 {
  color: #e8eeef;
  font-size: 1.5em;
  justify-content: center;
  align-items: center;
  display: flex;
}

header {
  display: flex;
  width: 550px;
  height: 70px;
  background: #AF7EEB;
  align-items: center;
}

.nav-title {
  justify-content: center;
  display: flex;
  width: 100%;
  margin-right: 40px;
}

.fas {
  color: #e8eeef;
  font-size: 25px;
  margin-left: 30px;
  cursor: pointer;
}
</style>
