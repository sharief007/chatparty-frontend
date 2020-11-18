<template>
  <div id="body">
    <div class="container">
      <div class="row">
        <div class="col-lg-10 col-xl-9 mx-auto">
          <div class="card card-signin flex-row my-5">
            <div class="card-img-left d-none d-md-flex">
              <!-- Background image for card set in CSS! -->
            </div>
            <div class="card-body">
              <h5 class="card-title text-center">Sign Up</h5>
              <form class="form-signin" @submit.prevent="login">
                <div class="form-label-group">
                  <input type="text" id="inputUserame" class="form-control" placeholder="Username" v-model="username" required autofocus>
                  <label for="inputUserame">Username</label>
                </div>

                <div class="form-label-group">
                  <input type="email" id="inputEmail" class="form-control" placeholder="Email address" v-model="email" required>
                  <label for="inputEmail">Email address</label>
                </div>

                <hr>

                <div class="form-label-group">
                  <input type="password" id="inputPassword" class="form-control" placeholder="Password" v-model="password" required>
                  <label for="inputPassword">Password</label>
                </div>

                <div class="form-label-group">
                  <input type="password" id="inputConfirmPassword" class="form-control" placeholder="Password" v-model="repeat" required>
                  <label for="inputConfirmPassword">Confirm password</label>
                </div>

                <button class="btn btn-lg btn-primary btn-block text-uppercase" type="submit">Register</button>
                <a class="d-block text-center mt-2 small" href="#">Sign In</a>
                <hr class="my-4">
                <button class="btn btn-lg btn-google btn-block text-uppercase" type="submit"><i class="fab fa-google mr-2"></i> Sign up with Google</button>
                <button class="btn btn-lg btn-facebook btn-block text-uppercase" type="submit"><i class="fab fa-facebook-f mr-2"></i> Sign up with Facebook</button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "Register",
  data(){
    return {
      username: '',
      email:'',
      password:'',
      repeat:''
    }
  },
  methods:{
    login(){
      let options = {
        headers: {'Content-Type':'application/json'}
      }
      axios.post('http://localhost:8080/register',{
        email:this.email,
        username: this.username,
        password: this.password
      },options).then((res) =>{
        console.log(res)
        this.$bvToast.toast(res.data._id,{
          title: 'Registration Successful',
          variant: 'success',
          autoHideDelay: 10_000,
          appendToast: true
        })
        //this.$router.push('/')
      })
    }
  }
}
</script>

<style scoped>
#body {
  width: 100%;
  height: 100%;
  background-color: #f2f2f2;
  overflow: auto;
}

body {
  background: #007bff;
  background: linear-gradient(to right, #0062E6, #33AEFF);
}

.card-signin {
  border: 0;
  border-radius: 1rem;
  box-shadow: 0 0.5rem 1rem 0 rgba(0, 0, 0, 0.35);
  overflow: hidden;
}

.card-signin .card-title {
  margin-bottom: 2rem;
  font-weight: 500;
  font-size: 1.5rem;
}

.card-signin .card-img-left {
  width: 45%;
  /* Link to your background image using in the property below! */
  background: scroll center url('https://images.pexels.com/photos/3127880/pexels-photo-3127880.jpeg');
  background-size: cover;
}

.card-signin .card-body {
  padding: 2rem;
}

.form-signin {
  width: 100%;
}

.form-signin .btn {
  font-size: 80%;
  border-radius: 5rem;
  letter-spacing: .1rem;
  font-weight: bold;
  padding: 1rem;
  transition: all 0.2s;
}

.form-label-group {
  position: relative;
  margin-bottom: 1rem;
}

.form-label-group input {
  height: auto;
  border-radius: 2rem;
}

.form-label-group>input,
.form-label-group>label {
  padding: 0.5rem 1.5rem;
}

.form-label-group>label {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  margin-bottom: 0;
  /* Override default `<label>` margin */
  line-height: 1.5;
  color: #495057;
  border: 1px solid transparent;
  border-radius: .25rem;
  transition: all .1s ease-in-out;
}

.form-label-group input::-webkit-input-placeholder {
  color: transparent;
}

.form-label-group input:-ms-input-placeholder {
  color: transparent;
}

.form-label-group input::-ms-input-placeholder {
  color: transparent;
}

.form-label-group input::-moz-placeholder {
  color: transparent;
}

.form-label-group input::placeholder {
  color: transparent;
}

.form-label-group input:not(:placeholder-shown) {
  padding-top: calc(0.75rem + 0.75rem * (2 / 3));
  padding-bottom: calc(0.75rem / 3);
}

.form-label-group input:not(:placeholder-shown)~label {
  padding-top: calc(0.75rem / 3);
  padding-bottom: calc(0.75rem / 3);
  font-size: 12px;
  color: #777;
}

.btn-google {
  color: white;
  background-color: #ea4335;
}

.btn-facebook {
  color: white;
  background-color: #3b5998;
}
</style>