<template>
	<!-- 我的分享  组件,这只是个组件,不是路由 -->
	<div class="myshare">
		<ul>
			<!-- 我的分享的跳转到详情页 -->
			<router-link :to="{name:'shareDetail',params:{id:index}}"tag="li" v-for="(project,index) in MShare" :key="index">
				<img :src="project.mpicUrl" alt="">
				<h2 class="shareTitle">{{project.title}}</h2>
				<p class="shareJianjie">{{project.jianjie}}</p>
			</router-link>
		</ul>
	</div>
</template>
<script>
	export default{
		name:'myshare',
		data(){
			return{
				MShare:[]

			}
		},
		created(){
		    var currentURL=this.HOST+'/data/mjson.json';
		    this.$axios.get(currentURL)
		    .then(res => {
		    	this.MShare = res.data.Mpics;
		    })
		    .catch(error => {
		      console.log(error);
		    })
		  }
	}
</script>
<style scoped lang="less">
.myshare{
	padding-bottom: 70/50rem;
	ul{
		width: 100%;
		background-color: #f6eaee;
		overflow: hidden;
		margin-bottom: 10/50rem;
		li{ 	
			background-color: #fff;
			width:45%;
			margin:10/50rem 0 0 12/50rem;
			overflow: hidden;
			img{
				width: 100%;
				height: 150/50rem;
			}
			.shareTitle{
				padding: 10/50rem 10/50rem;
				width: 60%;
				font-size: 14/50rem;
				font-weight: bold;
				white-space:nowrap;
				text-overflow: ellipsis;
				text-align: center;
				color: #333;
			}
			.shareJianjie{
				box-sizing: border-box;
				padding-left:5/50rem ;
			    text-indent: 0.6rem;
			    color: #999;
			    margin: 0.2rem 0;
			    line-height: 0.4rem;
			    margin-top: -0.1rem;
			    overflow: hidden;
			    text-overflow: ellipsis;
			    display: -webkit-box;
			    -webkit-line-clamp: 2;
			    -webkit-box-orient: vertical
			}

		}
	}

}

	
</style>