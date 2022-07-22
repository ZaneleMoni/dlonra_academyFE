<template>
<h1>Dlonra Academy</h1>
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
            <button id="register" class="btn btn-primary mt-4 signup" type="submit">
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

<style scoped>
* {box-sizing: border-box}
h1{
  font-family: montsserat;
}
h3{
  font-family: montsserat;
}
/* Add padding to containers */
.container1 {
  margin: 0 auto;
  padding: 16px;
  height: 50%;
  width:50%;
  box-shadow: 10px 17px 37px 0px rgba(0,0,0,0.75);
-webkit-box-shadow: 10px 17px 37px 0px rgba(0,0,0,0.75);
-moz-box-shadow: 10px 17px 37px 0px rgba(0,0,0,0.75);
}

/* Full-width input fields */
input[type=text], input[type=password] {
  width: 50%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #242323;
  border-radius:50px;
}

input[type=text]:focus, input[type=password]:focus {
  background-color: #ddd;
  outline: none;
}


/* Set a style for the submit/register button */
#register {
  background-color: #04AA6D;
  color: white;
  padding: 16px 20px;
  margin: 8px 0;
  border-radius: 50px !important;
  cursor: pointer;
  width: 20%;
  opacity: 0.9;
}

.register:hover {
  opacity:1;
}




</style>