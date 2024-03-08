<script setup>
import {computed, ref} from "vue";

   async function fetchUsers() { 
      const response = await fetch('https://jsonplaceholder.typicode.com/users').then(response => response.json())
      return response; 
    };

    const favUsers = ref([1, 3])
    const userList = await fetchUsers();

   function isUserFavouriteClass(userId) {
      if(this.favUsers.indexOf(userId) >= 0 ){
        return 'fav-user';
      }
    }
    function addFavouriteUser(userId){
      this.favUsers.push(userId); 
    }
</script>

<template>
  <main>
    <h1>User Page</h1>

    <div v-for="user in this.userList" :key="`user-${user.id}`" style="display:flex; justify-content: flex-start; padding-top: 20px;">
      {{ user.name }}
      <div v-if="isUserFavouriteClass(user.id)" style="margin-left: auto">
        ⭐
      </div>
      <div v-else  style="margin-left: auto">
        <button @click="addFavouriteUser(user.id)">Add to Favs</button>
        <button @click="addFavouriteUser(user.id)">Add to Favs</button>
      </div>
    </div>
  </main>
</template>

<style>
main {
  display: flex;
  justify-content: center;
  flex-direction: column;
  max-width: 320px;
  margin: 0 auto;
}

main h1 {
  margin-top: 10vh;
  margin-bottom: 20px;
}

label {
  margin-bottom: 5px;
}

input[type="email"] {
  padding: 0.5rem;
  margin-bottom: 30px;
}

button {
  border: 1px solid green;
  padding: 10px;
  color: green;
  background-color: rgb(213, 255, 213);
  cursor: pointer;
}
</style>
