<template>

  <div class="container">
    <h2>Articles Listing</h2>
    <a href="/articles/create" class="btn btn-success pull-right">Add New Article</a>

    <table class="table table-bordered">

      <thead>
        <tr>
          <th>ID</th>
          <th>Title</th>
          <th width="700">Content</th>
          <th>Action</th>
        </tr>
        <tr v-for="(article, index) in articles">
          <td>{{article.id}}</td>
          <td>{{article.title}}</td>
          <td>{{article.content}}</td>
          <td>
              <a :href="'/articles/'+article.id+'/edit'" class="btn btn-primary">Edit</a>
              <a href="javascript:void(0)" class="btn btn-danger" v-on:click="deleteArticle(article.id, index)">Delete</a>
          </td>
        </tr>
      </thead>

    </table>
  </div>


</template>


<script>
  export default{
    data(){
      return {
        articles:[],
        article:{
          id:0,
          name:'',
          email:''
        }
      }
    },
    mounted(){
      this.getArticles();
    },
    methods:{
      getArticles(){
          axios.get('/api/articles').then(response => {
            this.articles = response.data;
        })
      },
      deleteArticle(id, index){
        axios.delete('/api/articles/'+id).then(response => {
            console.log(response)
            this.articles.splice(index, 1)
        }).catch(error =>{
          console.log(error)
        })
      }
    }
  }
</script>


<style></style>
