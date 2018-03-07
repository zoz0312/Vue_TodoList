<template>
  <section>
    <ul>
      <li v-for="(todoItem, index) in propsdata" class="shadow">
        <i class="check-btn fa fa-check" aria-hidden="true"></i>
        {{ todoItem }}
        <span class="remove-btn" type="Button" @click="removeTodo( todoItem, index )">
          <i class="fa fa-trash-o" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>
export default{
  props: ['propsdata'],
  methods: {
    removeTodo( todoItem, index ) {
      this.$emit( 'removeTodo', todoItem, index );
    }
  }
}
</script>

<style>
  ul{
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }
  li{
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    padding: 0 0.9rem;
    margin: 0.5rem 0;
    background: white;
    border-radius: 5px;
  }
  .check-btn{
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }
  .remove-btn{
    margin-left: auto;
    color: #de4343;
  }
</style>
