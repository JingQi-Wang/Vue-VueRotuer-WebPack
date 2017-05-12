//content.vue
<template>
  	<div>
  		<div class="user">
		    <h1 class="logo">cnodejs Api Test</h1>		    
		    <ul class="list">
		      <li v-for="(item,index) in lists" v-text="item.title" v-on:click="alertText(index)"></li>
		    </ul>
		    <h2 v-on:click="look">{{ message }}</h2>
		    <div v-if="seen">想看见我吗</div>
		    <a href="#">返回</a>
			<a href="#/user/info">info.vue</a>
			<a href="#/user/love">info.vue</a>
		</div>
  	</div>
</template>
<script>
export default {
  data() {
    return {
    	message:"请点击我进行查看",
    	seen: false,
		lists:[]
    }
  },
  created () {
    // 组件创建完后获取数据，这里和1.0不一样，改成了这个样子
    this.get_data()
  },
  methods: {
    alertText: function (x) {
      	alert(x);      
    },
    look: function(){
    	let canlook = this.seen;
      	if(!canlook){
      		this.seen = true;
      	}else{
      		this.seen = false;
      	}
    },
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
