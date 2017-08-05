<template>
  <div id="tmpl">
			<ul class="mui-table-view">
				<li class="mui-table-view-cell mui-media" v-for="item in list">
                    <router-link v-bind="{to:'/news/newsinfo/'+item.id}">
						<img class="mui-media-object mui-pull-left" :src="item.img_url">
						<div class="mui-media-body">
							{{item.title}}
							<p class='mui-ellipsis'>{{item.zhaiyao}}</p>

                            <div class="info_b">
                                <span>发表时间：{{item.add_time | datefmt("YYYY-MM-DD HH:mm:ss")}}</span>
                                <span class="click">点击数：{{item.click}}</span>
                                
                            </div>
						</div>
                    </router-link>
				</li>


			</ul>
  </div>
</template>
<script>
import common from "../../kits/common.js"
export default {
  data:function(){
    return {
        list:[]
    }
  },
  created:function(){
    this.getNewsList()
  },
  methods:{
    getNewsList:function(){
       var url = common.apidomain+"/api/getnewslist";
       this.$http.get(url).then(function(reg){
           var data = reg.body;
           if(data.status !=0 ){
               alert(data.message);
               return
           }

           this.list = data.message
       })
    }
  }
}
</script>
<style scoped>
 .mui-table-view img{
 	height:80px;
    width:80px;
 }
  .mui-table-view .mui-media-object{
	 max-width: 80px;
	 line-height: 80px;
 }
.info_b{
    margin-top:1.5em;
    font-size: 12px;
    color:#0094ff;
}
.info_b .click{
    margin-left: 20px;
}
</style>

