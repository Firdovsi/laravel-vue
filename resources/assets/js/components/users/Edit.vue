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
        <div class="col-sm-10 col-sm-offset-2">
          <button class="btn btn-default" type="button" v-on:click="UpdateUser()">Save</button>
        </div>
      </div>

  </form>
</div>


</template>


<script>

export default {
    props:['id'],
    data(){
      return {
        name:'',
        email:'',
        password:''
      }
    },
    mounted(){
      axios.get('/api/users/'+this.id).then(response=>{
          var user = response.data;
          this.name = user.name;
          this.email = user.email;
      }).catch(error =>{
        console.log(error)
      })
    },
    methods:{
      UpdateUser(){
        axios.put('/api/users/'+this.id, {
          name:this.name,
          email:this.email
        }).then(response =>{
          console.log(response)
        }).catch(error =>{
          console.log(error)
        })
      }

    }
}

</script>




<style></style>
