<template>
  <div class="clear-all-contain">
    <span class="clear-all-btn" @click="clearTodo">Clear all</span>
  </div>
</template>

<script>
export default{
  methods: {
    clearTodo(){
      this.$emit('removeAll');      
    }
  }
}
</script>

<style scoped>
  .clear-all-contain{
    width: 8.5rem;
    height: 50px;
    line-height: 50px;
    background-color: white;
    border-radius: 5px;
    margin: 0 auto;
  }
  .clear-all-btn{
    display: black;
    color: #e20303;
  }
</style>
