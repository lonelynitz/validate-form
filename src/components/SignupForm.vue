<template>
  <div class="signupForm">
    <form @submit.prevent="handleSubmit">
      <label>Name</label>
      <input type="text"  v-model="uname">
      <label>Email</label>
      <input type="email"  v-model="email">
      <label>Password</label>
      <input type="password"  v-model="password">
      <div v-if="passwordError" class="error">{{ passwordError }}</div>
      <!--<label>Skills</label>
      <input type="text" v-model="skillsterms"> -->
      <div class="submit">
        <button>Create Account</button>
      </div>
      
    </form>
  </div>

  <div v-for="skil in skills" :key="skil" >
    <p>{{ skil }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      uname: '',
      email: '',
      password: '',
      skillsterms: '',
      skills: [],
      passwordError : ''
    }
  },
  methods : {
    addSkills(e) {
    if (e.key === ',' && this.skillsterms)
      if(this.skills.includes(this.skillsterms)){
        this.skills.push(this.skillsterms)
      }
      this.skillsterms = ''
    },
    handleSubmit(){
      this.passwordError = this.password.length > 5 ? '' : 'Password much contain more than 6 character!!'
    }
  }

}
</script>

<style>
form {
  background-color: white;
  border-radius: 10px;
  max-width: 500px;
  text-align: left;
  margin: 30px auto;
  padding: 30px;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 40px;
  font-size: 14px;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #aaa;
}
.submit button{
  background-color: blue ;
  padding: 10px 20px;
  color:  white;
  border-radius: 20px;
  border: none;
  margin-top: 10px;
}
.submit{
  text-align: center;
}
.error{
  color: red;
  margin-top: 3px;
}
</style>
