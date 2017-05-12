// src/page/user/info.vue
<template>
  <div>
  	<div class="user">
	    <h1 class="logo">cnodejs Api Test</h1>		    
	    <ul class="list">
	      <li v-for="(item,index) in lists" v-text="item.title" v-on:click="alertText(index)"></li>
	    </ul>   
	</div>
  </div>
</template>
