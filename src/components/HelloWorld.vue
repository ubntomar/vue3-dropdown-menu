<template>
  <div  v-for="menu in menus" :key="menu.id" >
    <p @click="toogleMenu(menu)" >{{menu.menuName}}</p>
      <div v-show="menu.visible" >
        <ul>
          <li>
            <a  href="{{menu.item[0].url}}">{{menu.item[0].name}}</a>  
          </li>
          <li>
            <a  href="{{menu.item[1].url}}">{{menu.item[1].name}}</a>  
          </li>
        </ul>
      </div>
  </div>
</template> 


<script setup  lang="ts">
  import {ref} from 'vue'
    const menus=ref([
          {
            id:1,
            menuName:'Menu 1',
            visible:false,
            item:[{name:'opc1',url:'/opc1'},{name:'opc2',url:'/opc2'}]
          },
          { 
            id:2,
            visible:false,
            menuName:'Menu 2',
            item:[{name:'mopc1',url:'/mopc1'},{name:'mopc2',url:'/mopc2'}]
          }
  ])
  const toogleMenu=(menu:any)=>{
      menu.visible=!menu.visible
      const id=menu.id
      menus.value.forEach(element=>element.id!==id?element.visible=false:element.visible)
  }
</script>

 
<style scoped>
  li {
    list-style-type: none; 
  }
  
  li a:active{
    color:goldenrod;   
  }
</style>
