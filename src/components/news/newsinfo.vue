<template>
  <div id="tmpl">
      <!--实现新闻详情  -->
      	<div class="title">
		   <h4>{{info.title}}</h4>
		   <p>{{info.add_time | datefmt("YYYY-MM-DD ")}} {{info.click}}</p>
	    </div>
		<div id="content" v-html="info.content">内容</div>
        <!--实现评论组件  -->
        <comment :id="id"></comment>
  </div>
</template>
<script>
import common from "../../kits/common.js"
//导入评论组件 comment.vue
import comment from '../subcom/comment.vue';
export default {
    components:{
        comment:comment
    },
  data:function(){
      return {
          id:0,
          info:{

          }
      }
  },
  created:function(){
      this.id = this.$route.params.id
      this.getinfo();

     
  },
  methods:{
      getinfo:function(){
        var url = common.apidomain+"/api/getnew/" + this.id;
        this.$http.get(url).then(function(reg){
            var data = reg.body;
             if(data.status !=0 ){
               alert(data.message);
               return
            }
            this.info = data.message[0]
        })
      }
  }
}
</script>
<style scoped>
	.title h4{
		color: #0094ff;
	}
	.title p{
		color:rgba(0,0,0,0.5);
	}

	.title,#content{
		padding: 5px;
	}
</style>



