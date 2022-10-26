<template>
    <ul>
      <li v-for="(item,i) in todoItem" :key="i" class="itemList">
        <div class="list">
          <i class="fa-regular fa-square-check"></i> 
          {{item}}
        </div>
        <div class="del" @click="removeDel(i,item)">
          <i class="fa-solid fa-eraser"></i>
        </div>
      </li>
    </ul>
  </template>
  
  <script>
  export default {
      props:[
          "todoItem"
      ],
      methods:{
        removeDel(num,item){
          this.$emit("reDel",num,item)
        }
      }
  }
  </script>
  
  <style lang="scss">
    .itemList {
      background: linear-gradient(90deg, #FDA085 0%, #F6D365 100%);padding: 20px;border-radius: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      height:35px;
      padding: 10px;
      margin-bottom: 5px;
      // background: pink;
      .list{
        display: flex;
        gap:10px;
        color: white;
      }
      .del{
        height: 100%;
        cursor:pointer;
        align-self:start;
        display: flex;
        justify-content: center;
        align-items: center;
        i{
          color: white;
        }
      }
    }
  </style>