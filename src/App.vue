<template>
  <div class="container">
    <h1>Todo List</h1>
    <FormTechno @add="save"/>
    <DisplayList :tech="technoArr" @deleteTech="testDelete"/>
  </div>
  
</template>

<script>
import { ref } from '@vue/reactivity';
import FormTechno from './components/FormTechno.vue';
import DisplayList from './components/DisplayList.vue';
export default {
  name: 'App',
  components: { FormTechno, DisplayList },

  setup(){

  let technoArr = ref([]) 

  const save = function(data){
    console.log("data",data);

    technoArr.value = [...technoArr.value, {techno: data, id: Date.now()}]
  }

  const testDelete = function(data){
    console.log("app", data);
    technoArr.value = technoArr.value.filter(t => t.id !== data.id)
  }
  
  return{
    save,
    technoArr,
    testDelete
  }
}
}


</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  background: #7E7EFF;
}

.container{
  margin-top: 100px;
  width: 30%;
  height: auto;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 20px;
  color: #fff;
 
}

 h1{
    padding-left: 10px;
    font-size: 35px;
  }
</style>
