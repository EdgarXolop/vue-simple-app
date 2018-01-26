<template>
  <div class="card" >
  <header class="card-header">
    <p class="card-header-title" v-text="post.title">
      
    </p>
    <a href="#" class="card-header-icon" aria-label="more options">
      <span class="icon">
        <i class="fas fa-angle-down" aria-hidden="true"></i>
      </span>
    </a>
  </header>
  <div class="card-content">
    <div class="content" v-text="post.body">
    </div>
  </div>
  <footer class="card-footer">
    <a href="#" @click="showHiddenData" class="card-footer-item">Save</a>
    <a href="#" @click="showHiddenData" class="card-footer-item">Edit</a>
    <a href="#" @click="showHiddenData" class="card-footer-item">Delete</a>
  </footer>
</div>
</template>
<script>
export default {
  props: {
    'chilaquil-post' : {
      type : Object,
      default : {userId : -1, id: -1}
    },
    'post-index' : {
      type: Number,
      default: -1
    }

  },
  name : 'post',
  data (){
      return {
        index : 0,
        post : {}
      }
  },
  methods: {
    showHiddenData () {
      alert('index  -> ' + this.index);
      alert('userId : '+this.post.userId + '\nid : ' + this.post.id);

    }
  },
  mounted () {
    this.post = this['chilaquilPost'];
    this.index = this['postIndex'];

    console.log()
  }
}
</script>
