<template>
<div id="app">
  <input
      type="text"
      placeholder="Search"
      class="search-input"
      v-model="searchValue"
  />
  <div class="users-container" v-if="usersList.length"
  v-for="(user, index) in usersList"
  :key="index"
  >
  {{ index+1 }}. {{ user.name }}
  </div>
  <div v-else >
    No users found for this search: {{ searchValue }}
  </div>

</div>
</template>


<script>
export default {
  name : 'App',
  components:{},
  data: () => ({
    searchValue:'',
    users: [
      {
        name:'Jhon',
        age:'45',
      }, {
        name:'Doe',
        age:'35',
      },
      {
        name:'Basit',
        age:'32',
      }, {
        name:'Jason',
        age:'38',
      },



    ]

  }),
  computed:{
    usersList(){
      if(this.searchValue.trim().length > 0){
        return this.users.filter((user) => user.name.toLowerCase().includes(this.searchValue.trim().toLowerCase()))
      }
      return this.users
    }
  }
}

</script>


<style scoped>
.search-input {
  width: 200px;
  height: 30px;
  border-radius: 5px;
}

</style>
