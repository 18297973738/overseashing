<template>
	<div class="buygoods">
		<div class="buycontent" >

		<ul class="navlist">
			<!-- <h5>{{navs.title}}</h5> -->
			<li v-for="(navs,index) in persList">
				<a href="javascript:;">
					<div class="img_list"><img :src="navs.img" alt="">
					</div><p>{{navs.title}}</p>
				</a>
			</li>
		</ul>	
		<ul class="goodslist" >
			{{idx}}
			<li  v-for="(item,index) in items">
				<router-link :to="{name:'Detaillist',params:{id:index}}">
				<a href="javascropt:;">
					<img :src="item.img" alt="">
					<p class="hot">
						<span class="hotbuy">{{item.hotbuy}}</span>
						<span class="liangping">{{item.liangping}}</span>
						<span class="gongxiao">{{item.gongxiao}}</span>
					</p>
					<div class="goodsdetail">
						<span class="money">{{item.money}}</span>
						<span class="dianzhan">{{item.number}}</span>
						<i class="iconfont icon-shoucang "></i>
					</div>
				</a>
				</router-link>
			</li>
		
		</ul> 
		</div>
	</div>
</template>
 <script>
export default{
	name:"Personcare",
	data(){	
		return{
			items:[],
			persList:[],
			navlist:[]
			
		}
}
,
 created(){
    console.log(this.$store.state.idx)
    var currentURL=this.HOST+'/data/buydata.json';
    this.$http.get(currentURL)
    .then(res => {
    	var str=this.$route.path.split('/').splice(3,1)+'';
    	if(str==0){
    		this.persList=res.data.personNav[0].navlist;
    	}else if(str==1){
    		this.persList=res.data.personNav[1].navlist;
    	}else if(str==2){
    		this.persList=res.data.personNav[2].navlist;
    	}else if(str==3){
    		this.persList=res.data.personNav[3].navlist;
    	}else if(str==4){
    		this.persList=res.data.personNav[4].navlist;
    	}else if(str==5){
    		this.persList=res.data.personNav[5].navlist;
    	}else{
    		return;    		
    	}
    	if(str==0){
    		 this.items =res.data.items[0].itemlist;
    	}else if(str==1){
    		 this.items =res.data.items[1].itemlist;
    	}else if(str==2){
    		 this.items =res.data.items[2].itemlist;
    	}else if(str==3){
    		 this.items =res.data.items[3].itemlist;
    	}else if(str==4){
    		 this.items =res.data.items[4].itemlist;
    	}else if(str==5){
    		 this.items =res.data.items[5].itemlist;
    	}else{
    		return

    	}

    })
    .catch(error => {
      // console.log(error);
    })
  },
  computed:{
			idx(){
				var Id=this.$route.path.split('/').splice(3,1)+'';
				this.$store.state.idx=Id;
		        // console.log(this.$store.state.idx)
			}
		
	},


}
	
</script>
<style scoped lang="less">
.buygoods{
	width: 100%;
	background: #F5F5F5;
	h5{
		color: 666666;
		font-size: 16/50rem;
		padding:10/50rem;
	}
	.navlist{
		overflow: hidden;
		width: 100%;
		background: #fff;
		li{
			width: 25%;
			padding:10/50rem 10/50rem;
			box-sizing: border-box;

			.img_list{
				width: 100%;
				border-radius: 50%;
				overflow: hidden;
				height: 74/50rem;
			}
			
			img{
				width:100%;

			}
			p{
				width: 100%;
				text-align: center;
				margin-top: 10/50rem;
				color: #666;
			}
		}
	}
	.goodslist{
		width: 100%;
		overflow: hidden;
		li{
			width: 46%;
			background: #fff;
			
			margin: 10/50rem 0;
			margin-left: 10/50rem;
			padding-bottom: 10/50rem;
			.hot{
				margin-top: 10/50rem;
			}
			.hotbuy{
			
				    background: #F9E4A8;
				    color: #333333; 
				    padding:5/50rem;
			}
			.liangping{

				    background: #FF743C;
				    color: #FFFFFF;
				    padding:5/50rem;
				    margin-left: 5/50rem;
			}
			.gongxiao{

			    background: #eff3f6;
			      padding:5/50rem;
			    color: #5a6f7a;
			     margin-left: 5/50rem;
			}
			img{
				width: 100%;
				height: 222/50rem;
			}
			.goodsdetail{
				margin-top: 20/50rem;
				overflow: hidden;
				padding: 0 5/50rem;
				box-sizing: border-box;
				span{
					float: left
				}
				.money{
					font-weight: 700;
					color: #333;
				}
				.dianzhan{
			    color: #999;
				float: right;
			}
			.iconfont{
				    color: #999;
				float: right;
			}

			}
			
		}
	}

}

	
</style>