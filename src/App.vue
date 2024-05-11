<template>
  <div id="app">
  <div v-for="i in pages" :key="i" class="homePage">
    <router-link :to="`${i.page}`">{{ i.name }}</router-link> |
  </div>
  <router-view />
</div>

</template>
<script>
export default{
  name:'homeWorld',
  data(){
    return{
      pages:[
        {
          id:1,page:'/home',name:'Home'
        },
        {
          id:1,page:'/about',name:'About'
        },
        {
          id:1,page:'/todoList',name:'To Do List'
        }
      ]
    }
  }
}
</script>
<style>
.homePage{
  display:flex;
  flex-direction: row;
}
</style>
