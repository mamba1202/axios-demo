<template>
  <div class="hello">
    <h3>我是axiosAPP，用来发送请求，拦截响应</h3>
    <button @click="getData">发送请求点击我得到conde社区数据</button>
  <ul>
  <li v-for="item in items">
  {{item.title}}
  </li>
  </ul>
  </div>
</template>

<script>
Vue.prototype.$http= axios; //将axios绑定到vue实例上，用$http访问
import axios from 'axios'
import Vue from 'vue'
export default {
  name: 'HelloWorld',
  data () {
    return {
      items:[]
    }
  },
  methods:{
    getData(){
      var self = this;
      this.$http.get('https://cnodejs.org/api/v1/topics?page=1&limit=15',)
     //对象形式传递参数 推荐使用
     //{
     //  params:{
     //   page: 1, 页码
     //  limit: 10 每页显示数量
     // } 
     // }
      .then(function(res){
        self.items=res.data.data  
        //此处的this指向不是当前vue实例 
        //或者用ES6语法 .then(res=>{})
         console.log(res.data.data)
      })
      .catch(function(err){
         console.log(err)
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
