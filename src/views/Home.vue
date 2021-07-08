<template>
  <h1>Все новости</h1>
  
  <div class="sections_list">
    <div v-for="(post,index) in posts" :key="post.id" class="section">
      <div class="section_params">
        <div class="section_id">
          {{index + 1}}
        </div>
        <div class="section_info">
          <div class="section_info__name" @click="activePost(index)" :class="{section_info__name_active: post.isActive}">
            {{post.title}}
          </div>
          <div class="section_info__userid">
            id автора: {{post.userId}}
          </div>
          <div class="section_info__body" v-show="post.isActive">
            {{post.body}}
          </div>
        </div>
      </div>
      <div class="section_actions">
        <button @click="deletePost(post.id, index)">Удалить</button>
      </div>
    </div>
  </div>
  <div class="loader" v-show="loader">
    <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="margin: auto; background: rgb(255, 255, 255); display: block; shape-rendering: auto;" width="200px" height="200px" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid">
      <circle cx="50" cy="50" r="32" stroke-width="8" stroke="#fe718d" stroke-dasharray="50.26548245743669 50.26548245743669" fill="none" stroke-linecap="round">
        <animateTransform attributeName="transform" type="rotate" repeatCount="indefinite" dur="1s" keyTimes="0;1" values="0 50 50;360 50 50"></animateTransform>
      </circle>
    </svg>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Home',
  data() {
    return {
      posts: [],
      loader: false
    }
  },
  mounted() {
    this.loader = true
    this.getPosts()
  },
  methods: {
    getPosts() {
      axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(({data})=> {
        this.posts = data.map( n => {
          return {
            ...n,
            isActive: false
          }

        })
        this.loader = false
      })
    },
    deletePost(id,index) {
      this.loader = true
      axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
      .then(()=> {
        this.posts.splice(index, 1)
        this.loader = false
      })
      
    },
    activePost(index) {
      console.log(index)
      this.posts[index].isActive = !this.posts[index].isActive
    }
  }
}
</script>

<style lang="less" scoped>
.sections_list {
  background: #fff;
}
.loader {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  opacity: 0.5;
  background: #000;

}
.section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  border-bottom: 1px solid #000;

  &_params {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  &_id {
    font-size: 4rem;
    margin-right: 30px;
  }
  &_info__name {
    cursor: pointer;
    font-weight: bold;
    transition: 0.2s linear;
    &:hover {
      color: #6d747e;
    }
    &_active {
      color: #3179e6;
      &:hover {
        color: #3179e6;
    }
    }
  }
  &_actions button{
    border: none;
    background: none;
    color: red;
    cursor: pointer;
  }
  &_info__body {
    margin-top: 30px;
  }
}
</style>
