<template>
    <div>
      <h2> Index page</h2>
      <div>{{name}}</div>
      <ul>
        <li><a href="/home">index 页</a></li>
      </ul>
      <div>
        <p>{{msg.name}}</p>
        <p>{{msg.age}}</p>
      </div>
  </div>
</template>
<script>
import axios from 'axios'
  export default{
    data() {
      return {
        name: 'name',
        list: []
      }
    },
    async asyncData(){
        let msg = await axios.get('https://api.myjson.com/bins/1b8ufm')
        return {
          msg: msg.data
        }
    }
  }
</script>