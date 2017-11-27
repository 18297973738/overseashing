<template>
	<div class="container">

		<div class="detailnav">
		    <span onclick="window.history.go(-1)">
		        <i class="iconfont icon-fanhui"></i>
		    </span> 
       	    <span class="toptitle">优惠券</span>
		</div>

		<div class="box">
			<div class="box_left">
				<span class="fuhao">¥</span><span class="price">5</span>
				<p class="content">买满50可使用</p>
			</div>
			<div class="box_right">
				<p class="name">
					<span class="dian">店铺东券</span><span class="xian">限购[心居专营店]</span>
				</p>
				<p class="dianpu">店铺商品</p>
				<p class="date">2017.12.19-2017.12.20</p>
			</div>	
		</div>
		<div class="box">
			<div class="box_left">
				<span class="fuhao">¥</span><span class="price">10</span>
				<p class="content">买满100可使用</p>
			</div>
			<div class="box_right">
				<p class="name">
					<span class="dian">店铺东券</span><span class="xian">仅限京东自营店</span>
				</p>
				<p class="dianpu">店铺商品</p>
				<p class="date">2017.12.19-2017.12.20</p>
			</div>	
		</div>
		<div class="box">
			<div class="box_left">
				<span class="fuhao">¥</span><span class="price">100</span>
				<p class="content">买满199可使用</p>
			</div>
			<div class="box_right">
				<p class="name">
					<span class="dian">店铺东券</span><span class="xian">限购[淘海购全球]</span>
				</p>
				<p class="dianpu">店铺商品</p>
				<p class="date">2017.12.19-2017.12.20</p>
			</div>	
		</div>
		<div class="box">
			<div class="box_left">
				<span class="fuhao">¥</span><span class="price">5</span>
				<p class="content">买满29可使用</p>
			</div>
			<div class="box_right">
				<p class="name">
					<span class="dian">店铺东券</span><span class="xian">仅限部分商品</span>
				</p>
				<p class="dianpu">店铺商品</p>
				<p class="date">2017.12.19-2017.12.20</p>
			</div>	
		</div>
		<div class="box">
			<div class="box_left">
				<span class="fuhao">¥</span><span class="price">30</span>
				<p class="content">买满49可使用</p>
			</div>
			<div class="box_right">
				<p class="name">
					<span class="dian">店铺东券</span><span class="xian">限购[美妆专营]</span>
				</p>
				<p class="dianpu">店铺商品</p>
				<p class="date">2017.12.19-2017.12.20</p>
			</div>	
		</div>

		
		</div>

	</div>
</template>
<script>
	export default{
		name:'youhuijian',
		data(){
			return{
				Order:[]
			}
		},
		created(){
			
		  }
	}
</script>
<style scoped lang="less">

.container{
	background-color: #FAFAFA;
	height: 100%;
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
	padding:10/50rem;
	overflow: hidden;
	height: 140/50rem;
}

.box_left,.box_right{
	float: left;
}
.box_left{
	width: 40%;
	height: 100%;
	background-color:#E6E6E6;
	text-align: center;
	color: white;
	padding: 20/50rem 0;
	box-sizing: border-box;
	.fuhao{
	margin-right:10/50rem;
}

.price{
	font-size: 40/50rem;
	font-weight: bold;
}
.content{
	font-size: 18/50rem;
	margin-top:20/50rem;
}
}


.box_right{
	padding: 10/50rem;
	box-sizing: border-box;
	background: #fff;
	height: 100%;
	.name{
		overflow: hidden;
		.dian{
			background:#E6E6E6;
			font-size: 14/50rem;
			display: inline-block;
			padding:5/50rem; 
			box-sizing: border-box;
			float: left;
		}
		.xian{
			font-size: 14/50rem;
			float: right;
			margin-left:15/50rem;
		}
		
	}
	.dianpu{
		margin:10/50rem 0;
	}
	.date{
		margin-top:30/50rem;
	}
}






</style>