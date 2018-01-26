<template>
  <div id="app" >
    <p>
      First Name
      <input type="text" v-model="firstName">
    </p> 
    <p>
      Last Name
      <input type="text" v-model="lastName" >
    </p> 

    <p v-text="firstName + ' ' + lastName" v-once></p>

    <p v-text="fullName" ></p>
    <p>
      <button @click="loadArray"  >Cargar datos</button>
    </p>

    <p>
      <div v-for="(post,$index) in posts">
        <chilaquil-post 
          :chilaquil-post="post"
          :post-index="$index">
        </chilaquil-post>
      </div>

    </p>

  </div>
</template>

<script>

import Post from './components/Post.vue'

export default {
  name: 'app',
  data () {
    return {
      content: '<h1>Proyeto Erica</h1>',
      firstName : 'Cristian',
      lastName : 'Sipac',
      posts : []
    }
  },
  methods : {
    loadArray (){
      let scope = this;
      
      this.$http.get('https://jsonplaceholder.typicode.com/posts').then(
      respose =>{
        scope.posts = respose.body;
      }, 
      response =>{
        console.log(respose);
      });
    }
  }
  ,
  computed: {
    fullName (){
      return this.firstName + ' ' + this.lastName;
    }
  },
  watch : {
    firstName (newVal, oldVal){
      // console.log(newVal, oldVal)
    }
  },
  components: {
    'chilaquil-post' : Post
  } 
}
</script>

