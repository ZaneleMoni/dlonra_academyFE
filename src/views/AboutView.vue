<template>


<table class="center" >
  <tr>
    <th>Email</th>
    <th>Name</th>
    <th>Surname</th>
  </tr>
  <tr v-for="user of users" :key="user.id">
    <td>{{user.email}}</td>
    <td>{{user.name}}</td>
    <td>{{user.surname}}</td>
  </tr>

</table>

  
</template>

<script>
export default {
data(){
  return {
    users: [],
    email:"",
    name:"",
    surname:""
  };
},

mounted(){
fetch("http://localhost:8000/users")
    .then((res) => res.json())
    .then((data) => {
      console.log(data)
      this.users = data.results;
    });
}
    }


</script>

<style>
table, th, td {
  border:1px solid black;
}
.center {
  margin-left: auto;
  margin-right: auto;
}
</style>
