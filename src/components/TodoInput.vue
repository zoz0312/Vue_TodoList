<template>
  <div class="input-box shadow">
    <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
    <span class="add-container" v-on:click="addTodo">
      <i class="add-btn fa fa-plus" aria-hidden="ture"></i>
    </span>
  </div>
</template>

<script>
export default{
  data(){
    return {
      newTodoItem: '',
    }
  },
  methods: {
    addTodo: function(){
      if ( this.newTodoItem !== "" ){
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodo', value);
        this.clearInput();
      }
    },
    clearInput(){
      this.newTodoItem = '';
    }
  }
}
</script>

<style>
  input:focus {
    outline: none;
  }
  .input-box {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .input-box input {
    border-style: none;
    font-size: 0.9rem;
  }
  .add-container {
    display: inline-block;
    float: right;
    width: 3rem;
    border-radius: 0 5px 5px 0;
    background: linear-gradient(to right, #6478FB, #8763FB);
  }
  .add-btn {
    color: white;
    vertical-align: middle;
  }
</style>
