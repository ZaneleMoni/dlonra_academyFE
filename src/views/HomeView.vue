<template>
   <div class="container1">
    <div class="row d-flex align-items-center justify-content-center">
      <div class="col-md-6">
        <div class="card2 px-5 py-5">
          <form class="formR" @submit.prevent="register">
            <h3 class="mt-3">Register Now<br /></h3>
            <div class="form-input">
              <i class="fa fa-user"></i>
              <input
                type="text"
                class="form-control"
                v-model="email"
                placeholder="Email"
                required
              />
            </div>
            <div class="form-input">
              <i class="fa fa-envelope"></i>
              <input
                type="text"
                class="form-control"
                v-model="name"
                placeholder="name"
                required
              />
            </div>
            <div class="form-input">
              <i class="fa fa-user"></i>
              <input
                type="text"
                class="form-control"
                v-model="surname"
                placeholder="surname"
                required
              />
            </div>
            <button class="btn btn-primary mt-4 signup" type="submit">
              Sign up!
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
data(){
    return {
        email: "",
        name:"",
        surname:""
    }
},
methods:{
        register(){
      console.log(this.email,this.name, this.name);
      fetch("http://localhost:8000/register", {
        method:"POST",
        body:JSON.stringify({
          email:this.email,
          name:this.name,
          surname:this.surname,
        }),
        headers:{
          "Content-type":"application/json;charset=UTF-8",
        },
      })
      .then((res)=>res.json())
      .then((user)=>{
        console.log(user);
        alert("User registered");
        localStorage.getItem("jwt",user.jwt);
      })
      .catch((err)=>{
        alert(err);
      });
    },
}
}

</script>

<style>

</style>