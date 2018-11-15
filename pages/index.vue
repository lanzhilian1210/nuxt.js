<template>
    <div>
      <h2> Index page</h2>
      <div>{{name}}</div>
      <ul>
        <li><a href="/home">index 页</a></li>
      </ul>
      <div>
        {{msg}}
      </div>
      <ul>
        <li v-for="(item,index) in info" :key="index">
          <p>{{item.checkHospital}}</p>
          <p>{{item.bloodPressure}}</p>
          <p>{{item.checkTime}}</p>
          <p>{{item.openId}}</p>
        </li>
      </ul>
  </div>
</template>
<script>
  import axios from 'axios'
  export default{
    data() {
      return {
        name: '1232',
        list: []
      }
    },
    async asyncData(){
        let list = await axios.post('http://47.104.101.207:8080/checkInfo/selectCheckInfo',{"id":125})
        let msg = await axios.get('https://api.myjson.com/bins/1b8ufm')
        return {
          info: list.data.data,
          msg: msg.data
        }
    }
  }
</script>