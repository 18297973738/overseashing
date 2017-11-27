<template>
	<div class="shoppingCar">
		<div class="detailnav">
		    <span onclick="window.history.go(-1)">
		        <i class="iconfont icon-fanhui"></i>
		    </span> 
       	    <span class="toptitle">购物车</span>
    	</div>
    	<div class="box">
			<div class="carCont" v-for="(item,index) in carData">
				<p class="shopTitle"> <i class="icon iconfont icon-dianpu"></i>{{item.shopTitle}} &nbsp;&nbsp;&nbsp;&gt;</p>
				<div class="shopCont">
					<div class='shopImg'><img :src="item.shopImg" alt=""></div>
					<div class="shopJianjei">
						<p class="jianjei">{{item.jianjie}}</p>
						<!-- Couter组件 -->
						<p class="price"><span>￥{{item.price}}</span> <span>
							<div class="counter-component">
								<div class="counter-btn" @click="minus(index)"> - </div>		
								<div class="counter-show">
									<input type="text" v-model="item.num" @keyup="getNumber(index)">
								</div>
								<div class="counter-btn" @click="adds(index)"> + </div>
							</div>
						</span>
					</p>
					</div>
				</div>
			</div>
		</div>
		<div class="shoppingFooter">
			<span>合计: {{count}}</span>
		</div>
	</div>
</template>
<script>
import "../../../assets/css/font/iconfont.css";
	export default{
		name:'shoppingCar',
		data(){
			return{
				flag:true,
				carData:[],
				count:0,
				max:20,
				min:1

			}
		},
		created(){
			var currentURL=this.HOST+'/data/mjson.json';
		    this.$axios.get(currentURL)
		    .then(res => {
		    	this.carData = res.data.carData;
		    	// console.log(this.carData)
		    })
		    .catch(error => {
		      console.log(error);
		    })
		},
		methods:{
			selectd:function(event){
				this.flag = !this.flag;
			},
			minus(key){
				this.carData[key].num--;
				if(this.carData[key].num<= this.min){
					this.carData[key].num= this.min
				}
				this.carData[key].total=this.carData[key].num*this.carData[key].price;
				this.count=0;
				for(var i=0;i<this.carData.length;i++){
					this.count+=parseInt(this.carData[i].total)
				}
			},
				adds(key){
					this.carData[key].num++;
					if(this.carData[key].num >= this.max){
						this.carData[key].num = this.max
					}
					this.carData[key].total=this.carData[key].num*this.carData[key].price;
					this.count=0;
					for(var i=0;i<this.carData.length;i++){
						this.count+=parseInt(this.carData[i].total)
					
					}
				
					
				},
				getNumber(key){
					// 快速输入
					let finalNum;
					if(typeof this.carData[key].num  === "string"){
						finalNum = Number(this.carData[key].num.replace(/\D/g,""));
					}else{
						finalNum = this.carData[key].num;
					}
					if(finalNum > this.max || finalNum<this.carData[key].num){
						finalNum = this.max;
					}else{
						
					}
					this.carData[key].num = finalNum;
				}
	
		}
	}
</script>
<style scoped lang="less">
.shoppingCar{
	width: 100%;
	background-color: #EEEEEE;
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
	.carCont{
		width: 100%;
		background-color: #F5F5F5;
		box-sizing: border-box;
		.shopTitle{
			height: 45/50rem;
			background-color: #fff;
			line-height: 50/50rem;
			font-size: 16/50rem;
			padding: 0 45/50rem;
			margin-top:15/50rem;
			i{
				padding-right: 10/50rem;
				font-size: 18/50rem;
				color: #FF6B9F;
			}
		}
		.shopCont{
			padding: 5/50rem 15/50rem 15/50rem 45/50rem ;
			background-color: #F5F5F5;
			overflow: hidden;
			
			.shopImg{
				width:100/50rem;
				height: 2rem;
				float: left;
				margin-right: 10/50rem;
				img{
					width: 100%;
				}
			}
			.shopJianjei{
				font-size: 14/50rem;
				line-height: 120%;
				.jianjei{
					margin: 10/50rem 0 15/50rem;
					color: #333;
				}
				.price{
					color:  #FF6B9F;
					span:nth-of-type(1){
						float: left;
					}
					span:nth-of-type(2){
						float: right;
					}

				}
			}
			
		}
	}
	.box{
		margin-bottom: 60/50rem;
	}
	.shoppingFooter{
		position: fixed;
		bottom: 0;
		height: 1rem;
		width: 100%;
		background-color: #fff;
		font-size: 16/50rem;
		text-align: center;
		line-height: 1rem;
		span:nth-of-type(1){
			display: block;
			height: 100%;
			background-color: #FF6B9F;
			color: #fff;

		}

	}
}
.counter-component {
  position: relative;
  display: inline-block;
  overflow: hidden;
  vertical-align: middle;
}
.counter-show {
  float: left;
}
.counter-show input {
  border: none;
  border-top: 1px solid #e3e3e3;
  border-bottom: 1px solid #e3e3e3;
  height: 25/50rem;
  line-height: 25/50rem;
  width: 30/50rem;
  outline: none;
  text-indent: 4/50rem;
  text-align: center;
}
.counter-btn {
  border: 1px solid #ddd;
  float: left;
  height: 25/50rem;
  line-height: 25/50rem;
  width: 25/50rem;
  text-align: center;
  cursor: pointer;
}
.counter-btn:hover {
  border-color: #FF6B9F;
  background: #FF6B9F;
  color: #fff;
}	
</style>