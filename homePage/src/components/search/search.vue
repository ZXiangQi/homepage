<template>
  <div id="search" class="clearfix">
    <div class="engine">
      <div class="selected">{{selected}}</div>
      <ul>
        <li v-for="(link, key) in searchList" @click="changeEngine(key)">{{key}}</li>
      </ul>
    </div>
    <form :action="formAction" target="_blank" @submit.prevent="onSubmit" ref="form">
      <input type="text" v-model="searchText" :name="formName">
      <input type="submit" value="搜 索">
    </form>
  </div>  
</template>

<script type="text/javascript">
  export default {
    name: 'search',
    data: function() {
      return {
        searchList: {
          '百度': {link: 'https://www.baidu.com/baidu?word', name: 'word'},
          '必应': {link: 'http://cn.bing.com/search?q', name: 'q'},
          '搜狗': {link: 'https://www.sogou.com/web?query', name: 'query'},
          '谷歌': {link: 'https://www.google.com/search?q', name: 'q'}
        },
        selected: '百度',
        searchText: ''
      }
    },
    computed: {
      formAction: function() {
        return this.searchList[this.selected].link + this.searchText
      },
      formName: function() {
        return this.searchList[this.selected].name
      }
    },
    methods: {
      changeEngine: function(key) {
        this.selected = key
      },
      onSubmit: function() {
        var form = this.$refs.form
        form.submit()
      }
    }
  }
</script>

<style type="text/css">
  #search{
    width: 400px;
    margin: 0 auto;
  }
  #search .engine{
    position:relative;
    height: 20px;
    width: 60px;
    float: left;
    padding: 10px 0;
    text-align: center;
    line-height: 1;
    border: 1px solid #B8B8B8;
    font-size: 18px;
    cursor: pointer;
  }
  #search .engine ul{
    display: none;
    width: 100%;
    position: absolute;
    top: 40px;
    left: -1px;
    text-align: center;
    border: 1px solid #B8B8B8;
    background: #fff;
    z-index: 10;
  }
  #search .engine:hover ul{
    display: block;
  }
  #search .engine ul li{
    height: 20px;
    padding: 5px 0;
  }
  #search .engine ul li:hover{
    background: #3388FF;
    color: #fff;
  }
  #search form{
    float: left;
    font-size: 0;
  }
  #search form input[type="text"] {
    width: 250px;
    height: 40px;
    padding: 0 5px;
    font-size: 18px;
    border: 1px solid #B8B8B8;
    border-left: none;
    border-right: none;
  }
  #search form input[type="submit"] {
    width: 70px;
    height: 42px;
    font-size: 18px;
    background: #3388FF;
    color: #fff;
    cursor: pointer;
  }
  #search form input[type="submit"]:hover {
    background: #317EF3;
  }
</style>