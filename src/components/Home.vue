<template>
    <div>

      <router-link to="/list/1">Go to list1</router-link><br>
      <router-link to="/list/2">Go to list2</router-link><br>

    </div>
</template>

<script>
    export default{
        data(){
            return {
                msg: 'hello vue'
            }
        }
    }
</script>

<style scoped>
    body {
        background-color: #ff0000;
    }
  h1{
    font-size: 30px;
  }
</style>