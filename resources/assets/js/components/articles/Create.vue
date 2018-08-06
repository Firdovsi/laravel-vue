<template>

  <div class="container">
    <h2>Add New Article</h2>

    <form class="form-horizontal" action="/users" method="POST">
        <div class="form-group">
          <label class="control-label col-sm-2" for="title">Title:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="title" placeholder="Enter title" name="title" v-model="title">
          </div>
        </div>
        <div class="form-group">
          <label class="control-label col-sm-2" for="email">Email:</label>
          <div class="col-sm-10">
            <textarea class="form-control" id="content" placeholder="Enter Content" name="content" v-model="content"></textarea>
          </div>
        </div>

        <div class="form-group">
          <div class="col-sm-10 col-sm-offset-2">
            <button class="btn btn-default" type="button" v-on:click="addNewArticle()">Add Article</button>
          </div>
        </div>

    </form>
  </div>


</template>


<script>
  export default  {
    data(){
      return {
        title:'',
        content:''
      }
    },
    methods:{
      addNewArticle(){

        axios.post('/api/articles', {

          title:this.title,
          content:this.content

        }).then(response=>{
          console.log(response)
          this.title = '';
          this.content = '';
        }).catch(error =>{
          console.log(error)
        })
      }
    }
  }

</script>


<style></style>
