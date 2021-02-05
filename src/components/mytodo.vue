<template>
     <div id="myContainer">
       <h3> {{title}}</h3> 
       <div class="info">
           <p>Double click to mark task completed</p>
           <p>completed</p>
           <p>Incomplete</p>
       </div>
          <div id="grid">
                 <div :class="{'Done':todo.isDone}" @dblclick="markasDone(todo)"  class="inComplete" v-for="(todo,index) in todos"  :key='todo.id'>
                        {{todo.title}}
                         <!-- {{todo.isEdited}}   -->
                        <i class="fas fa-edit" v-if="!todo.isEdited && !todo.isDone" @click="EditTodo(index,todo)"></i>
                        <button v-if="todo.isEdited " @click="updateTodo(index,todo)">Update</button>
                        <i class="fas fa-trash-alt" @click="deleteTodo(index)"></i>
                 </div> 
          </div>
     </div>
</template>

<script>
export default {
    props:['todos','inputText'],
    data(){
        return{
            title:'MyTodos'
        } 
    },
    methods:{
        deleteTodo:function(index){
            this.todos.splice(index,1);
        },
        markasDone:function(todo){
            todo.isDone = !todo.isDone;
        },
       EditTodo:function(index,todo){
           this.$emit('changeTitle',todo.title)
        //    this.inputText = todo.title;
           todo.isEdited = true;
            // alert(this.inputText);
        } ,
        updateTodo:function(index,todo){
            todo.isEdited = false;
            todo.title = this.inputText ;
            this.$emit('emptyinputText');
        }
    }
}
</script>


<style scoped>
 #grid{
     display: grid;
     grid-template-columns: repeat(3,1fr);
     grid-gap: 1rem;
     
 }
 .inComplete{
     text-align: center;
     background: #37BC61;
     padding: 1rem;
     border-radius: 10px;
     cursor: pointer;
     position: relative;
 }
.fa-trash-alt {
    color: #fff;
    position: absolute;
    bottom: 10px;
    right: 12px;
 }
.fa-edit {
    color: #fff;
    position: absolute;
    bottom: 10px;
    right: 29px;
 }
button {
    color: rgb(0, 0, 0);
    position: absolute;
    bottom: 7px;
    right: 29px;
 }
 .fa-trash-alt:hover{
    color:red;
 }
 .fa-edit:hover{
    color:red;
 }
 button:hover{
    color:red;
 }
 .info{
     display: flex;
     justify-content: space-around;
 }
 .info p{
    /* flex-grow: 1; */
    margin:0px 14px 10px 10px;
    position: relative;
 }
 .info p:nth-child(2):before{
      margin:0px px 10px 10px;
    content: '';
    position: absolute;
    left:-17px;
    top: 6px;
    width: 15px;
    height: 15px;
    background: #3d3b58;
 }
 .info p:nth-child(3):before{
      margin:0px px 10px 10px;
   content: '';
    position: absolute;
    left:-17px;
    top: 6px;
    width: 15px;
    height: 15px;
    background:  #37BC61;
 }
 .Done{
     background: #504e6f;
 }
</style>
