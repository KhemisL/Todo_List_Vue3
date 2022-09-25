<template>
  <ul>
    <li v-for="techno in tech" :key="techno.id">
        <div class="content">
            <button class="edit" @click="funcTechno(techno)"><img src="../assets/icons8-edit.svg" alt=""></button>
        <span class="content-save" v-if="modifyTechno !== null && modifyTechno.id === techno.id">
            <input class="text" type="text" v-model="modifyTechno.techno">
            <button class="save" @click="save" ><img src="../assets/save-svgrepo-com.svg" alt=""></button>
        </span>
        <span class="text" v-else>
            {{techno.techno}} 
        </span>
        </div>
        
        <button class="del" @click="$emit('deleteTech', techno)"><img src="../assets/icons8-delete.svg" alt=""></button>
        
    </li>
  </ul>
</template>

<script>
import { ref } from '@vue/reactivity'

export default {

    emits: ["deleteTech", "modifyTech"],
    props: {
        tech: {
            type:Array,
            requiered: true
        }
    },

    

    setup(){

        let modifyTechno = ref(null)

        const funcTechno = (techno)=>{
            modifyTechno.value = techno
        }

        const save = ()=> {
            modifyTechno.value = null
        }
        return{
            modifyTechno,
            funcTechno,
            save
        }
    }

    
}
</script>

<style>
   ul{
    width: 100%;
    padding: 20px;
    list-style: none;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
   }

   ul li{
    width: 86.8%;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 5px 0px;
    border-radius: 5px;
    box-shadow: 10px 5px 15px 0px rgba(0, 0, 0, 0.233);
    background: #3333FF;
   }

   ul li .del{
    display: flex;
    align-items: center;
    justify-content: center;
    border-left: 1px solid #fff;
    font-size: 18px;
    font-weight: 700;
    
   }

   .content input{
    border: none;
    outline: none;
    font-size: 16px;
    width: 60%;
    transition: 1s ease-in;
    color: #fff;
    background: #3333FF;
   }
   .content img{
    width: 28px;
   }
   .content .save{
    position: relative;
    top: 2px;
   }

   .content .text{
    font-size: 18px;
    position: relative;
    top: -4px;
   }
   .save img{
    width: 25px;
   }

   ul li .del{
    justify-self: flex-end;
    border-left: 1px solid #fff;
    font-size: 18px;
    font-weight: 700;
   }
   ul li .edit{
    border-right: 1px solid #fff;
    font-size: 16px;
    font-weight: 700;
    margin-right: 15px;
   }

   ul li button{
    border: none;
    background: none;
    color: #000;
    height: 50px;
    width: 50px;
    cursor: pointer;
   }

</style>