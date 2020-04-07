<template>
  <div>
    <div @click="toggleNav" :class="{open2: isOpen}" id="nav-icon1">
      <span></span>
      <span></span>
      <span></span>
    </div>
    <div class="nav" :class="{open: isOpen}">
      <transition-group class="side-nav" tag="ul" name="slide-in" appear>      
        <li class="nav-link" v-for="(link, index) in links" :key="link" @click="toggleNav; changeSelected(index)" :class="{'selected': selected === index}">{{ link }}</li>
      </transition-group>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'sideNav',
    props: {
      links: {
        type: Array,
        default: []
      },
    },
    data() {
      return {
        isOpen: false,
        selected: 0
      }
    },
    methods: {
      toggleNav() {
        this.isOpen = !this.isOpen
      },
      changeSelected(index) {
        this.selected = index
      }
    },
  }
</script>

<style scoped>

#nav-icon1 {
  position: absolute;
  top: 20px;
  left: 20px;
  width: 30px;
  height: 30px;
  -webkit-transform: rotate(0deg);
  -moz-transform: rotate(0deg);
  -o-transform: rotate(0deg);
  transform: rotate(0deg);
  -webkit-transition: .5s ease-in-out;
  -moz-transition: .5s ease-in-out;
  -o-transition: .5s ease-in-out;
  transition: .5s ease-in-out;
  cursor: pointer;
  z-index: 3;
}

#nav-icon1 span {
  display: block;
  position: absolute;
  height: 0.2px;
  width: 100%;
  background-color: #fff;
  border-color: #5E5E5E;
  border-radius: 9px;
  opacity: 1;
  left: 0;
  -webkit-transform: rotate(0deg);
  -moz-transform: rotate(0deg);
  -o-transform: rotate(0deg);
  transform: rotate(0deg);
  -webkit-transition: .5s ease-in-out;
  -moz-transition: .5s ease-in-out;
  -o-transition: .5s ease-in-out;
  transition: .5s ease-in-out;
}

#nav-icon1 span:nth-child(1) {
  top: 5px;
}

#nav-icon1 span:nth-child(2) {
  width: 23px;
  top: 15px;
}

#nav-icon1 span:nth-child(3) {
  top: 25px;
}

#nav-icon1.open2 span:nth-child(1) {
  opacity: 1;
  top: 18px;
  -webkit-transform: rotate(135deg);
  -moz-transform: rotate(135deg);
  -o-transform: rotate(135deg);
  transform: rotate(135deg);
}

#nav-icon1.open2 span:nth-child(2) {
  opacity: 0;
  left: -60px;
}

#nav-icon1.open2 span:nth-child(3) {
  top: 18px;
  -webkit-transform: rotate(-135deg);
  -moz-transform: rotate(-135deg);
  -o-transform: rotate(-135deg);
  transform: rotate(-135deg);
}

/* ------ Transition Styles -------- */

.slide-in-enter {
  opacity: 0;
  transform: translateX(-50px);
}

.slide-in-enter-active,
.slide-in-leave-active {
  transition: all 0.5s ease-in-out;
}

.slide-in-leave {
  opacity: 0;
  transform: translateX(50px);
}

/* --------------------------------- */

ul {
  padding: 0;
  margin: 0;
}

li {
  list-style-type: none;
}

.nav {
  position: absolute;
  top: 0;
  left: 0;
  height: 100vh;
  max-height: 100vh;
  background: #000;
  width: 0;
  overflow: hidden;
  display: flex;
  justify-content: center;
  transition: all 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  z-index: 1;
}

.nav.open {
  width: 25%;
}

.side-nav {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}

.nav-link {
  font-size: 1.6rem;
  letter-spacing: 0.02em;
  font-weight: bold;
  cursor: pointer;
  color: #fff;
  position: relative;
}

.nav-link.selected {
  color: #4bcffa;
}

.nav-link:after{
  content: '';
  position: absolute;
  width: 0; height: 12px;
  display: block;
  background: #2b70dc;
  transition: width .2s ease;
  -webkit-transition: width .2s ease;    
  bottom: 0;
  left: 0;
  z-index: -1;
}
 
.nav-link:hover:after{
  width: 100%;
  left: 0;
  background: #2b70dc;
}


span {
  margin: 0 5px;
  border: 2px solid black;
  cursor: pointer;
}

</style>