<template>
    
 <div id="myContainer">
    <form class="myform">
           <input type="text" v-model="inputText" placeholder="Add Todo...." required/>
           <button type="submit" @click.prevent="addTodo">Submit</button>         
    </form>
     <mytodos v-bind:todos="todos" v-on:changeTitle="updateTodo($event)"  v-on:emptyinputText="emptyinputText()" :inputText="inputText" ></mytodos>
 </div>


</template>

<script>
import mytodos from './mytodo.vue'


export default {
    components:{
        'mytodos':mytodos,
    },
    data(){
        return{
            inputText:'',
            todos:[
                {
                    title:'completing Vue js,Vuetify,VueX',
                    isDone:false,
                     isEdited:false
                   
                },
                {
                    title:'Learning Python and Django',
                    isDone:false,
                    isEdited:false
                },
                {
                    title:'Practicing Data Structurs and Algorithm',
                    isDone:false,
                    isEdited:false
                },
                {
                    title:'Trying To Develope Competitive Coding',
                    isDone:false,
                    isEdited:false
                },
            ]
        }
    },
    methods:{
        addTodo:function(){
            var newTodo ={
                title:this.inputText,
                isDone:false,
                isEdited:false
            }
            this.todos.push(newTodo);
            this.inputText='';
        },
        updateTodo:function(updatedTodo){
               this.inputText = updatedTodo;
            //    alert('updated in parent')
        },
        emptyinputText:function(){
            this.inputText ='';
        }
    }
}
</script>


<style scoped>

      .myform{
         display: flex;

      }
      input{
          outline: 0;
          border:1.3px solid#0E8C3A	;
          padding:0.6rem 1rem;
          flex-basis: 70%;

      }
      button{
          color:#fff;
           outline: 0;
           border: 0;
          padding:0.6rem 1rem;
          flex-basis: 18%;
          background:#37BC61;
      }
</style>