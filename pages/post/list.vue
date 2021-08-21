<template>
    <div class="text-center mt-5 mb-5" > 
    <h1 class="mb-3">Post List</h1>
    <b-card
    v-for="post in posts" :key="post.id"
    :title="post.title"
    img-src="https://picsum.photos/600/300/?image=25"
    img-alt="Image"
    tag="article"
    style="max-width: 75rem;"
    class="mb-2 mt-2"
  >
    <b-card-text>
     {{post.body}}
    </b-card-text>
   <b-button href="#" variant="primary" @click="viewDetails(post.id)">View Details</b-button>
  </b-card> 
</div>
</template>
<script>
import {mapState} from 'vuex'
export default {
 name: 'PostList',
 async fetch({store, $axios, error}){
  try{
 const {data} = await $axios.get('/posts');
 store.dispatch('setPosts', data);
  }catch(err){
    error({statusCode: 500, message: 'Oops, something went wrong'})
  }
},
   computed: {
  ...mapState({
    posts: state => state.post.posts
  }) 
},
methods: {
  viewDetails(postId){
    this.$router.push({path: `/post/${postId}/details`})
  }
}

    
}
</script>