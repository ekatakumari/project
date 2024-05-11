<template>
  <div class="search">
    <input class="input-search" type="text" name="" id="" v-model="searchQuery" @input="search">
    <ul>
      <li class="list-item" v-for="item in filteredSearch " :key="item.id">
         <span v-html="highlightData(item.name)"></span>
      </li>
      <li v-if="filteredSearch.length==0" class="no-found">no search found</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return{
      searchQuery:'',
      items:[
        {
          id:1,name:'hello',
        },
        {id:2,name:'hello'},
        {id:3,name:'hello'},
        {id:4,name:'data'}
      ]
    }
  },
  computed:{
    filteredSearch(){
       return this.items.filter(item=>{
          return item.name.toLowerCase().includes(this.searchQuery.toLowerCase())
        })
    },
  },
  methods:{
   search(event){
    this.searchQuery=event.target.value
   },
   highlightData(text){
    if(!this.searchQuery) return text
    let regex=new RegExp(`${this.searchQuery}`,'gi')
    console.log(regex)
    return text.replace(regex,`<span class="highlight">${text}</span>`)
   }
  }
}
</script>
<style scoped>
.search{
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width:400px;
}
.input-search{
width:100%;
height:30px;
border:2px solid orange;
border-radius:3px;

}
.list-item{
 font-size: 20px;
 margin-top: 5px;

}
ul{
  list-style-type:none;
  height:400px;
  border: 2px solid orange;
  width:100%;
  
}
.highlight{
  color:red;
}
.no-found{
  font-size: 20px;
  margin:5px;
  color: orange;
}
</style>
