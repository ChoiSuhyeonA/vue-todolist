<template>
  <section>
    <ul>
      <!-- v-for를 사용할때는 반드시 key값을 연결해줘야 한다. -->
      <li v-for="(todoItem, index) in propsdata" v-bind:key="index" >
         <i class="checkBtn fas fa-check" aria-hidden="true"></i>
         {{ todoItem }} 
         <span class="removeBtn" type="Button" @click="removeTodo(todoItem, index)">
           <i class ="far fa-trash-alt" aria-hidden="true"></i>
         </span>
      </li>
       
    </ul>
  </section>
</template>

<script>
export default {
  props:['propsdata'],
  methods:{
    addTodo(){
      var value = this.newTodoItem && this.newTodoItem.trim();
      this.$emit('addTodo', value);
      
    },
    removeTodo(todoItem, index){
     this.$emit('removeTodo', todoItem, index);
    }
  }
}
</script>

<style>
  ul{
    /* 리스트에 점을 없애준다. */
    list-style-type: none; 
    padding-left: 0px;
    margin-top: 0;
    text-align: left; 
    margin-left: 10px;
  }
  li{
    display: flex;
    min-height:30px;
    height:50px;
     line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 20px;
  }

  .checkBtn{
    line-height: 45px;
    color:rgb(7, 177, 126);
    margin-left: 30px;
    margin-right: 70px;
  }

  .removeBtn{
    margin-left:auto;
    color:rgb(245, 9, 213)
  }
</style>