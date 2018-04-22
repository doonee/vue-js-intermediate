<template>
  <section class="inputBox">
      <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
      <!-- <button v-on:click="addTodo" class="addBtn">add</button> -->
      <span class="addContainer" v-on:click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
  </section>
</template>

<script>
export default {
    data () {
        return {
            newTodoItem: ""
        }
    },
    methods: {
        addTodo () {
            if(this.newTodoItem !== '') {
                var obj = {
                    completed: false,
                    item: this.newTodoItem
                }
                localStorage.setItem(this.newTodoItem, JSON.stringify(obj))       
                this.clearInput()
            }
        },
        clearInput () {
            this.newTodoItem = ''
        }
    }
}
</script>

<style scoped>
input:focus {
    outline: none;
}
.inputBox {
    background: #fff;
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
    background: linear-gradient(to right, #6478fb, #8763fb);
    display: block;
    width: 3rem;
    border-radius: 0, 5px 5px 0;
}
.addBtn {
    color: #fff;
    vertical-align: middle;
}
</style>
