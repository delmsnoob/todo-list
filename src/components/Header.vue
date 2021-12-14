<template>
  <header>
    <i class="fas fa-bars"></i>
    <div class="header__nav">
      <h2>{{ text }}</h2>
    </div>
  </header>    
</template>

<script>
export default {
  name: 'Header',
  props: {
    text: String
  }
}
</script>

<style scoped>
header {
  display: flex;
  /* justify-content: center; */
  align-items: center;
  height: 70px;
  background: #af7eeb;
}

.fas {
  color: #fff;
  font-size: 1.5em;
  cursor: pointer;
  margin-left: 30px;
  
}

.header__nav {
  justify-content: center;
  align-items: center;
  display: flex;
  width: 100%;
  margin-right: 40px;
}

h2 {
  color: #fff;
  font-size: 1.4em;
}
</style>