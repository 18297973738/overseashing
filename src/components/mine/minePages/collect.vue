<template>
	<div class="container">

		<div class="detailnav">
		    <span onclick="window.history.go(-1)">
		        <i class="iconfont icon-fanhui"></i>
		    </span> 
       	    <span class="toptitle">我的收藏</span>
		</div>
		<div class="box">
			<ul >
				<li class="boxlist" v-for="(item,index) in Collect" :key="index">
					<p class="img"><img :src="item.img" alt=""></p>
					<p class="title">{{item.title}}</p>
					<p>
						<span class="price">{{item.price}}</span>
						<span class="common">找相似</span>
					</p>
				</li>
			</ul>
			
		</div>
	
	</div>
</template>
<script>
	export default{
		name:'collect',
		data(){
			return{
				Collect:[]
			}
		},
		created(){
			var currentURL=this.HOST+'/data/message.json';
		    this.$axios.get(currentURL)
		    .then(res => {
		    	this.Collect = res.data.xinxi;
		    	console.log(this.Collect);
		    })
		    .catch(error => {
		      console.log(error);
		    })
		  }
	}
</script>
<style scoped lang="less">

.container{
	background-color: #eee;
	width: 100%;
	height: 100%;
	overflow: hidden;
}
.detailnav{
		width: 100%;
		background: #FF6B9F;
		position: relative;
		overflow: hidden;
		text-align: center;
		padding:20/50rem 0px;
		color: #fff;
		font-size: 18/50rem;
		.toptitle{
			display: inline-block;
			width:120/50rem;
			text-overflow: ellipsis;
			white-space: nowrap;
			vertical-align: top;
			overflow:hidden;
			}
			.icon-fanhui{
			position: absolute;
			left:14/50rem;
			top:20px;
			color: #fff;
			font-size: 20/50rem;
		}
}
.box{
	width: 100%;
	margin-top: 10/50rem;
	background-color: #eee;
	ul{
		width: 100%;
		overflow: hidden;
		.boxlist{
			background: #fff;
			width: 45%;
			float: left;
			margin-left:12/50rem;
			padding-bottom:20/50rem;
			margin-bottom: 20/50rem;
			border-radius: 5/50rem;
			.img{
				width: 100%;
				height:130/50rem;
				overflow: hidden;
			}
			img{
				width: 100%;
			}
			.title{
				   width:80%;
				   padding:10/50rem;
		          text-overflow: ellipsis;
		          white-space: nowrap;
		          vertical-align: top;
		          overflow:hidden;
			}
			p{
				overflow: hidden;
				padding: 10/50rem;
				.price{
					float: left;
					color: #FF5900;
				}
				.common{
					float: right;
					padding-right: 10/50rem;
				}
			}
		}
	}
}








</style>