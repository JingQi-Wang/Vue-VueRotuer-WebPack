//index.vue
<template>
  	<div>
		<div class="index">
		    <h1 class="logo">cnodejs Api Test</h1>
		    <ul class="list">
		      <li v-for="item in lists" v-text="item.title"></li>
		    </ul>
		    <a href="#/content">点我跳转</a>
	    </div>
  	</div>
</template>
<script>
export default {
  data() {
    return {
      lists:[]
    }
  },
  created () {
    // 组件创建完后获取数据，这里和1.0不一样，改成了这个样子
    this.get_data()
  },
  methods: {
    get_data: function(params) {
      var v = this
      if (!params) params = {}
      // 我们这里用全局绑定的 $api 方法来获取数据，方便吧~
      v.$api.get('topics', params, function(r) {
        v.lists = r.data
      })
    },
  },
}
</script>