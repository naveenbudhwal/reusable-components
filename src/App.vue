<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> | 
      <router-link to="/side-nav">Side Nav</router-link>
    </div>
    <transition name="slide-fade" mode="out-in">
      <router-view/>
    </transition>
  </div>
</template>

<style>

/* * {
  margin: 0;
  padding: 0;
} */

/* -------- Trasition Styles ------- */

.slide-fade-enter {
  opacity: 0;
  transform: translateX(50px);
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.3s ease-in-out;
}

.slide-fade-leave {
  opacity: 0;
  transform: translateX(-50px);
}

/* --------------------------------- */

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  font-family: Noah, sans-serif;
}

#nav {
  padding: 30px;
  text-align: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  font-size: 1.2rem;
}

#nav a.router-link-exact-active {
  color: #2b70dc;
}
</style>
