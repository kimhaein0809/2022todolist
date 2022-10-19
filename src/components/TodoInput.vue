<template>
    <div class="todoWrap">
      <div class="tp"></div>
      <div class="sq">
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
          <i class="fa-solid fa-square"></i>
      </div>
      <div class="Wrap">
        <h1>TO DO LIST</h1>
        <div class="searchInput">
          <input
            type="text"
            class="inp"
            placeholder="오늘의 할일을 입력하세요"
            v-model="newTodoItem"
          />
          <button class="btn" @click="todoItem">+</button>
        </div>
      </div>
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
  h1{text-align: center;margin-bottom: 30px;color: white;}
  h1:after{
    content:"";
    display: block;
    width: 100px;
    height: 2px;
    background: white;
    margin: 0 auto;
    margin-top: 10px;
  }
  .todoWrap{
    background: linear-gradient(90deg, #FDA085 0%, #F6D365 100%);padding: 20px;border-radius: 10px;
            position: relative;
            box-shadow: 5px 5px 0px 0px #FDA085;
            .tp{
              width: 40px;height: 50px;position: absolute;background: #FDA085;
            top: 50px;right: -40px;border-radius: 0 5px 5px 0;
            box-shadow: 5px 20px 0px 0px #ff7852;
            }
            .sq{
              color: white;font-size: 25px;
            display: flex;justify-content: space-between;
            margin-bottom: 15px;
            }
  }
  .searchInput {
    width: 300px;margin: 10px auto;gap: 5px;
    display: flex;
    .inp {
      width: 300px;
      flex-grow: 1;text-indent: 10px;border: none;border-radius: 5px;
    }
    .inp:focus {
      outline-color: #ffc149;
    }
    .btn {
      width: 40px;height: 40px;
      cursor: pointer;
      background: white;
      border: none;
      border-radius: 5px;
      color: #ffc149;
      font-size: 30px;
    }
  }

  
  .mView-enter-from{opacity: 0;transform:translateY(100%)}
  .mView-enter-active{transition:0.3s}
  .mView-enter-to{opacity: 1;transform:translateY(0)}
  
  .mView-leave-from{opacity: 1;}
  .mView-leave-active{transition:0.3s}
  .mView-leave-to{opacity: 0;}
  
  </style>