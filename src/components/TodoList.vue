<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
        <i class="fas fa-check checkBtn" v-bind:class="{checkBtnCompleted: todoItem.completed}" 
          v-on:click="toggleComplete(todoItem, index)"></i>
        <span v-bind:class="{textCompleted : todoItem.completed}">{{ todoItem.item }}</span>
        <!-- <button v-on:click="removeTodo">delete</button> -->
        <span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
          <i class="fas fa-trash"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {  
    // data: function() {
    //   return {
    //     todoItems: [],
    //   }
    // },
    props: ['propsdata'],
    methods: {
      removeTodo: function(todoItem, index) {
        this.$emit('removeItem', todoItem, index);
      },
      toggleComplete: function(todoItem, index) {
        this.$emit('toggleItem', todoItem, index);
      }
    },
    // created: function() {
    //   // console.log("created");
    //   if (localStorage.length > 0) {
    //     for (let i = 0; i < localStorage.length; i++) {
    //       // console.log(localStorage.key(i))
    //       if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
    //         // this.todoItems.push(localStorage.key(i))
    //         // localStorage.getItem(localStorage.key(i));
    //         // console.log(JSON.parse(localStorage.getItem(localStorage.key(i))));
    //         this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
    //       }
    //     }
    //   }
    // }
  }
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0px;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background-color: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
</style>