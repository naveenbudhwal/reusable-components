<template>
  <div>
    <h1>Some reusable components</h1>
    <hr class="material-hr">
    <h3 class="comp-name">Tag Input</h3>
    <tag-input />
  </div>
</template>

<script>
import tagInput from '@/components/tagInput.vue';
  export default {
    components: {
      tagInput
    }
  }
</script>

<style scoped>

.comp-name {
  text-align: left;
  margin-left: 10%;
}

.material-hr {
  height: 6px;
  border-radius: 3px;
  width: 15em;
  border: none;
  background: #2b70dc;
  margin-bottom: 3em;
}

</style>