<template>
	<header>
		<div class="inner clearfix">
      <h1>我的导航</h1>
      <search></search>
    </div>
	</header>
</template>

<script type="text/javascript">
import Search from '../search/search'

export default {
  name: 'header',
  components: {
    Search
  }
}
</script>

<style type="text/css">
  header{
    width: 100%;
    height: 60px;
    background: #fff;
    box-shadow: 0px 2px 2px 1px #eee;
  }
  header .inner{
    width: 80%;
    margin: 0 auto;
    padding: 10px 0;
  }
  header h1{
    float: left;
    line-height: 1.5;
    font-size: 28px;
  }
</style>