<template>
  <div class="input-box shadow">
    <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
    <span class="add-container" v-on:click="addTodo">
      <i class="add-btn fa fa-plus" aria-hidden="ture"></i>
    </span>

    <modal v-if="showModal" @close="showModal=false">
      <h3 slot="header">Alert!</h3>
      <span slot="footer" @click="showModal=false">
        Please write to do!
        <i class="closeModalBtn fa fa-times" aria-hidden="true"></i>
      </span>
    </modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue';

export default{
  props: ['propsdata'],
  data(){
    return {
      newTodoItem: '',
      showModal: false,
    }
  },
  methods: {
    addTodo: function(){
      if ( this.newTodoItem !== "" ){
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodo', value);
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput(){
      this.newTodoItem = '';
    }
  },
  components: {
    Modal: Modal
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
