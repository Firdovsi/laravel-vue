<template>
<div class="container">
  <h2>Edit Article</h2>

  <form class="form-horizontal" action="/articles" method="POST">
      <div class="form-group">
        <label class="control-label col-sm-2" for="title">Title:</label>
        <div class="col-sm-10">
          <input type="text" class="form-control" id="title" placeholder="Enter Title" name="title" v-model="title">
        </div>
      </div>
      <div class="form-group">
        <label class="control-label col-sm-2" for="content">Content:</label>
        <div class="col-sm-10">
          <textarea class="form-control" id="content" placeholder="Enter content" name="content" v-model="content"></textarea>
        </div>
      </div>
      <div class="form-group">
        <div class="col-sm-10 col-sm-offset-2">
          <button class="btn btn-default" type="button" v-on:click="UpdateArticle()">Update Article</button>
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
        title:'',
        content:''
      }
    },
    mounted(){
      axios.get('/api/articles/'+this.id).then(response=>{
          var article = response.data;
          this.title = article.title;
          this.content = article.content;
      }).catch(error =>{
        console.log(error)
      })
    },
    methods:{
      UpdateArticle(){
        axios.put('/api/articles/'+this.id, {
          title:this.title,
          content:this.content
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
