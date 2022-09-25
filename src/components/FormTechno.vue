<template>
  <form @submit.prevent="addTechno">
    <label for="techno">Nouvelle Liste </label>
    <div class="wrapper">
      <input type="text" name="techno" v-model="technoLearn">
      <button type="submit">Ajouter</button>
    </div>
    
  </form>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
    setup(props, ctx){
        let technoLearn = ref("") 

        const addTechno = ()=>{
            ctx.emit("add",technoLearn.value)
            technoLearn.value = ""
        }

        
        return{
            technoLearn,
            addTechno,
        }
    }
}
</script>

<style>
  form{
    display: flex;
    flex-direction: column;
    width: 100%;
    padding: 20px;
    justify-content: flex-start;
    align-items: flex-start;
    height: 10vh;
    font-size: 18px;
    color: #fff;
    font-weight: 700;
  }

  .wrapper{
    display: flex;
    width: 100%;
    margin-top: 30px;
  }

  .wrapper input{
    border: 1px solid #7070FF;
    height: 45px;
    width: 60%;
    outline: none;
    font-size: 16px;
    padding-left: 20px;
    border-radius: 5px 0px 0px 5px;
  }
  .wrapper button{
    outline: none;
    padding: 0px 35px;
    border-radius: 0px 5px 5px 0;
    font-weight: 900;
    cursor: pointer;
    border: 1px solid #7070FF;
    background: #3333FF;
    color: #fff;
  }
</style>