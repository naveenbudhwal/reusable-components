<template>
  <div class="tag-input">
    <transition-group name="slide-in" appear>
      <div v-for="(tag, index) in tags" :key="tag" class="tag-input__tag">
        <span @click="removeTag(index)">x</span>
        {{ tag }}
      </div>
    </transition-group>
    <button id="cta" @click="sortTags()">Sort</button>
    <input 
      type='text' 
      placeholder="Enter a Tag" 
      class='tag-input__text'
      @keydown.enter = 'addTag' 
      @keydown.188 = 'addTag'
      @keydown.delete = 'removeLastTag'
    />
  </div>
</template>

<script>
  export default {
    data() {
      return {
        tags: ['Hello', 'World']
      }
    },
    methods: {
      addTag(event) {
        event.preventDefault()
        let val = event.target.value.trim()
        if(val.length > 0) {
          this.tags.push(val)
          event.target.value = ''
        }
      },
      removeTag(index) {
        this.tags.splice(index, 1)
      },
      removeLastTag(event) {
        if(event.target.value.length === 0) {
          this.removeTag(this.tags.length - 1)
        }
      },
      sortTags() {
        this.tags.sort()
      }
    }
  }
</script>

<style scoped>

/* ----------- Transition styles ---------- */
.slide-in-enter {
  opacity: 0;
  transform: translateX(20px);
}

.slide-in-enter-active,
.slide-in-leave-active {
  transition: all 0.3s ease-in-out;
}

.slide-in-leave {
  opacity: 0;
  transform: translateX(-20px);
}

.slide-in-move {
  transition: all 0.3s ease-in-out;
}

/* ---------------------------------------- */

.tag-input {
  width: 80%;
  margin-left: 10%;
  border: 1px solid #ddd;
  border-radius: 10px;
  font-size: 0.9em;
  height: 50px;
  box-sizing: border-box;
  padding: 0 10px;
  display: flex;
}

.tag-input__tag {
  height: 30px;
  float: left;
  margin-right: 10px;
  background-color: #eee;
  margin-top: 10px;
  line-height: 30px;
  padding: 0 5px;
  border-radius: 5px;
}

.tag-input__tag > span {
  cursor: pointer;
  opacity: 0.75;
}

.tag-input__text {
  border: none;
  outline: none;
  font-size: 0.9em;
  line-height: 50px;
  background: none;
}

#cta {
  border: none;
  height: 30px;
  margin-top: 10px;
  border-radius: 5px;
  background: #000;
  color: #fff;
  margin-right: 10px;
  cursor: pointer;
}

</style>