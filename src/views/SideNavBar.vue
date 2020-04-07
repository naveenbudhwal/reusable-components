<template>
  <div>
    <side-nav :links="links"/>
  </div>
</template>

<script>
  import SideNav from '@/components/SideNav.vue';
  export default {
    name: 'sideNavBar',
    components: {
      SideNav,
    },
    data() {
      return {
        links: ['Dashboard', 'Links', 'Visualisations', 'Settings']
      }
    },
  }
</script>

<style scoped>

</style>