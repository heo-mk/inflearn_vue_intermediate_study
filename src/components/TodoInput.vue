<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <!-- <button v-on:click="addTodo">add</button> -->
    <span class="addContainer" v-on:click="addTodo">
      <i class="fas fa-plus addBtn"></i>
    </span>

    <Modal v-if="showModal" @close="showModal = false">
    <!--
      you can use custom content here to overwrite
      default content
    -->
      <h3 slot="header">경고임!</h3>
    </Modal>
  </div>
</template>

<script>
  import Modal from "./common/Modal.vue" 

  export default {
    data: function() {
      return {
        newTodoItem: "",
        showModal: false,
      }
    },
    methods: {
      addTodo: function() {
        // console.log(this.newTodoItem);
        if (this.newTodoItem !== '') {
          // let obj = {
          //   completed: false,
          //   item: this.newTodoItem,
          // };
          // // 저장하는 로직
          // // localStorage.setItem(this.newTodoItem, obj);
          // localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
          // this.$emit('이벤트 이름', 인자1, 인자2, ...)
          this.$emit('addTodoItem', this.newTodoItem);
          this.clearInput();
        } else {
          this.showModal = !this.showModal;
        }
      },
      clearInput: function() {
        this.newTodoItem = "";
      },
      components: {
        Modal: Modal,
      }
    }
  }
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background-color: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0px 5px 5px 0px;
}
.addBtn {
  color: white;
  vertical-align: middle;
  z-index: 3;
}
</style>