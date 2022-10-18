<template>
    <div class="searchInput">
      <input
        type="text"
        class="inp"
        placeholder="오늘의 할일을 입력하세요"
        v-model="newTodoItem"
      />
      <div class="btn" @click="todoItem">할일</div>
    </div>
  
    <transition name="mView">
      <modal v-if="modalView" @click="modalView = false">
        <template v-slot:header>경고</template>
        <template v-slot:body>자료를 입력하세요</template>
      </modal>
    </transition>
  
  
  </template>
  <script>
  import Modal from "@/components/Modal.vue";
  
  export default {
    components: { Modal },
  
    data() {
      return {
        newTodoItem: "",
        modalView: false,
      };
    },
    methods: {
      todoItem() {
        if (this.newTodoItem != "") {
          let value = this.newTodoItem && this.newTodoItem.trim();
          this.$emit("addTodo", value);
          // this.newTodoItem = document.querySelector(".inp").value;
        } else {
          // alert("오늘의할일을 입력하세요")
          this.modalView = true;
        }
        this.newTodoItem = "";
      },
    },
  };
  </script>
  
  <style lang="scss">
  .searchInput {
    display: flex;
    .inp {
      flex: 1 0 auto;
      text-indent: 10px;
    }
    .btn {
      line-height: 40px;
      padding: 0 10px;
      background: gray;
      color: white;
      cursor: pointer;
    }
  }
  
  .mView-enter-from{opacity: 0;transform:translateY(100%)}
  .mView-enter-active{transition:0.3s}
  .mView-enter-to{opacity: 1;transform:translateY(0)}
  
  .mView-leave-from{opacity: 1;}
  .mView-leave-active{transition:0.3s}
  .mView-leave-to{opacity: 0;}
  
  </style>