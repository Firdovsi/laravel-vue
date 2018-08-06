<template>

  <div class="container">
    <h2>Add New User</h2>

    <form class="form-horizontal" action="/users" method="POST">
        <div class="form-group">
          <label class="control-label col-sm-2" for="name">Name:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="name" placeholder="Enter Name" name="name" v-model="name">
          </div>
        </div>
        <div class="form-group">
          <label class="control-label col-sm-2" for="email">Email:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="email" placeholder="Enter Email" name="email" v-model="email">
          </div>
        </div>
        <div class="form-group">
          <label class="control-label col-sm-2" for="pwd">Password:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="pwd" placeholder="Enter Password" name="pwd" v-model="password">
          </div>
        </div>
        <div class="form-group">
          <div class="col-sm-10 col-sm-offset-2">
            <button class="btn btn-default" type="button" v-on:click="addNewUser()">Save</button>
          </div>
        </div>

    </form>
  </div>


</template>


<script>
  export default  {
    data(){
      return {
        name:'',
        email:'',
        password:''
      }
    },
    methods:{
      addNewUser(){

        axios.post('/api/users', {

          name:this.name,
          email:this.email,
          password:this.password

        }).then(response=>{
          console.log(response)
          this.name = '';
          this.email = '';
          this.password = '';
        }).catch(error =>{
          console.log(error)
        })
      }
    }
  }

</script>


<style></style>
