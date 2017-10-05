<template>
  <div id="app">
    <v-header></v-header>
    <div id="content">
      <ul>
        <li v-for="(item, title) in linkData" class="linkSection">
          <h3 class="title">{{title}}</h3>
          <ul class="linkList">
            <li v-for="(link, key) in item">
              <a :href="link" target="_blank" :title="key">{{key}}</a>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Header from './components/header/header'
import linkData from './data.json'

export default {
  name: 'app',
  data: function() {
    return {
      linkData: linkData
    }
  },
  components: {
    'v-header': Header
  }
}
</script>

<style>
  #app{
    width: 100%;
    height: 100%;
    background: #eee;
  }
  #content{
    width: 80%;
    margin: 0 auto;
    padding: 10px;
  }
  #content .linkSection{
    margin: 10px 0 20px;
    background: #fff;
    box-shadow: 1px 2px 4px #999;
  }
  #content .linkSection .title{
    height: 30px;
    padding: 0 10px;
    line-height: 30px;
    background: #403E4E;
    color: #fff;
  }
  #content .linkSection .linkList{
    padding: 10px;
  }
  #content .linkSection .linkList li{
    display: inline-block;
  }
  #content .linkSection .linkList li a{
    display: block;
    width: 100px;
    height: 30px;
    margin: 0 10px;
    padding: 0 10px;
    line-height: 30px;
    border-radius: 5px;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
    text-align: center;
    background: #DADCDB;
  }
  #content .linkSection .linkList li a:hover{
    background: #E1E1E1;
    color: #fff;
  }
</style>
