<!-- 以后项目的根组件 -->
<template>
	<div>
		<!--利用mint-ui中的header组件实现整个系统的头部  -->
        <mt-header fixed title="Vue商城系统demo"></mt-header>
		<!--利用vue-router的<router-view>占位  -->
		<router-view></router-view>
		<!--利用mui实现整个系统的底部  -->
		<nav class="mui-bar mui-bar-tab">
			<router-link class="mui-tab-item " to="/home">
				<span class="mui-icon mui-icon-home"></span>
				<span class="mui-tab-label">首页</span>
			</router-link>
			<router-link class="mui-tab-item" to="/tabbar-with-chat">
				<span class="mui-icon mui-icon-email">
				
				</span>
				<span class="mui-tab-label">会员</span>
			</router-link>
			<router-link class="mui-tab-item" to="/shopcar">
				<span class="mui-icon mui-icon-contact">
					<span class="mui-badge">0</span>
				</span>
				<span class="mui-tab-label">购物车</span>
			</router-link>
			<router-link class="mui-tab-item" to="/tabbar-with-map">
				<span class="mui-icon mui-icon-gear"></span>
				<span class="mui-tab-label">搜索</span>
			</router-link>
		</nav>
	</div>
</template>

<script>


	import { Toast } from 'mint-ui';

	
	export default{  
	
	}
</script>

<style scoped>


</style>