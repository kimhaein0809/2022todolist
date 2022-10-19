<template>
  <div class="clearAll" @click="$emit('clearAll')">
    CLEAR ALL
  </div>
</template>

<script>
export default {

}
</script>

<style>
  .clearAll{
    display: flex;
    justify-content: center;
    align-items: center;
    background: 
    linear-gradient(90deg, #FDA085 0%, #F6D365 100%);
    color: white;
    height: 35px;
    margin-top: 20px;
    border-radius: 10px;
    cursor: pointer;
    box-shadow: 5px 5px 0px 0px #FDA085;

  }
</style>