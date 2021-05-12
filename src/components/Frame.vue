<template>
  <div class="frame">
    <ol>
      
        <p class="a">TODO</p>
      
    </ol>
    <div >
      <input placeholder="Nova Nota" v-model="newTodo" v-on:keyup.enter="addTodo1()"/>
      <div>
        <button v-on:click="addTodo1()">Adicionar Tarefas</button>
        <button v-on:click="removeAll()">Remover Tarefas Completas</button>
      </div>
      <div class="a">
    
    
    <ul class="todos__list">
        <li class="todos__item" v-for="todo in todos" v-bind:key="todo.id" :class="{ 'todos__completed': todo.completed }" @click="todo.completed = !todo.completed">
        <p class="a" @click=" DoneElement()">{{ todo.text }}
        <img class="todos__delete" style="img" alt="X" src="../assets/X.png" v-on:click.stop="removeElement(todo.id-1)" />
        </p>

        </li>
    </ul>
    
    </div>
    </div>
  </div>
</template>

<script>

export default {
		name: 'App',
        data() {
            
        return {
        newTodo: '',
        todos: [{ id: 1, text: "Aprender VueJs", completed: false },{ id: 2, text: "Pagar Contas", completed: false},{ id: 3, text: " Ver TV", completed: false },
                { id: 4, text: "Comer Janta", completed: false },{ id: 5, text: "Beber agua", completed: false },{ id: 6, text: " ", completed: false }
        ],
        
        };
    },
    computed: {
    
    itemsDone() {
      return this.todos.filter(todo => todo.completed)
    },
    
    itemsTodo() {
      return this.todos.filter(todo => !todo.completed)
    }
  },
		methods: {
            addTodo1() {
            // create new todo object
            const newEntry = {
            id: this.todos.length + 1,
            text: this.newTodo,
            completed: false };

            // if input field not empty...
            if (this.newTodo.length) {
            // ...push to todos array 
            this.todos.push(newEntry);
            // ...reset input field
            this.newTodo = '';
      }
    },
            addTodo(text) {
                
                 if (text !== null) {
                    this.todos.push({
                        id: this.todos.length + 1,
                        text,
                    });
                }
            
    
            },
            removeAll() {
            this.todos = this.itemsTodo;
            },
             removeElement(index){
            this.todos.splice(index,1);
            },
            DoneElement(){
              this.todos.completed = !this.todos.completed;
            
            }

        },
        
	}
</script>

<style>
div.frame {
  align-content: center;
  align-self: center;
  justify-content: center;
  
  width: 511px;
  -webkit-box-shadow: 10px 9px 17px -5px rgba(0,0,0,0.55);
  -moz-box-shadow: 10px 9px 17px -5px rgba(0,0,0,0.55);
  box-shadow: 10px 9px 17px -5px rgba(0,0,0,0.55);
  border-radius: 10px 10px 10px 10px;
-moz-border-radius: 10px 10px 10px 10px;
-webkit-border-radius: 10px 10px 10px 10px;
border: 0px solid #000000;

}
App{
    justify-self: center;
  align-self: center;
}

.todos__completed {
  background: #f6feff;
  text-decoration: line-through;
  color: rgb(54, 170, 0);
}

img{
    height: 25px;
    width: 25px;
    
}
ul {list-style-type: square;}


p.a{
  font-size: 25px;
  text-decoration-line: none ;
  padding-top: 15px;
}
p.b{
  font-size: 25px;
  text-decoration-line: none ;
}


input{
  height: 25px;
  width: 275px;
  align-content: center;
  justify-content: center;
}



</style>
