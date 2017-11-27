<template>	
	<div class="detaillist">
    <div class="detailnav">
		   <span onclick="window.history.go(-1)">
		        <i class="iconfont icon-fanhui"></i>
		      </span> 
       <span class="toptitle">{{detaillist.title}}</span>
    </div>
    <div class="detail_content">
    	<img :src="detaillist.img" alt="">
    	<p class="userinfo"> 
			<img class="user_icon" :src="detaillist.userinfo" alt="">
    	<span class="user">MAKO</span>
    	<span class="attetion" v-if="val"  @click="open('top')">
        <i >+</i>关注</span>
      <span v-else="val" @click="close('top')" class="attetion changeattetion">已关注</span>
    	</p>
      <div class="gz">
      <mu-popup position="top" v-if="val1"  :overlay="false" popupClass="demo-popup-top" :open="topPopup">关注成功</mu-popup>
      <mu-popup position="top" v-else="val1" :overlay="false" popupClass="demo-popup-top" :open="topPopup">取消关注</mu-popup>
  </div>  
    	<p class="detail">
    		{{detaillist.detail}}
    	</p>
    	
    </div>
    <div class="footer">
    	<p class="zhan" @click="attetion" > 
    		<i class="iconfont icon-xin" :class="flag?'active':''"></i>
    	   <span>赞·<i> {{zanNum}}</i></span>
    	</p>
    	<p class="argument">
	    	<i class="iconfont icon-weibiaoti11"></i>
	    	<span>评论·{{detaillist.argument}}</span>
    	</p>
    	<p class="cllect" @click="collect" :class="cllect?'collectActive':''">
	    	<i class="iconfont icon-shoucang" :class="cllect?'collectActive':''"></i>
	    	<span>收藏·{{collectNum}}</span>	
        {{idx}}
    	</p>
    </div>
  </div>
</template>
<script>

	export default{
		name:"Detaillist",
		data(){
			return{
				detaillist:[],
          topPopup: false,
          val:true,
          val1:true,
          flag:false,
          zanNum:0,
          cllect:false,
          collectNum:0


			}
		},
		created(){
		    // console.log("组件创建后")
		    var currentURL=this.HOST+'/data/buydata.json';
		    this.$http.get(currentURL)
		    .then(res => {
          
      if(this.$store.state.idx==0){
        this.detaillist=res.data.items[0].itemlist[this.$store.state.detailId];
        console.log(this.detaillist)
      }else if(this.$store.state.idx==1){
        this.detaillist=res.data.items[1].itemlist[this.$store.state.detailId];
         console.log(this.detaillist)
      }else if(this.$store.state.idx==2){
        this.detaillist=res.data.items[2].itemlist[this.$store.state.detailId];
         console.log(this.detaillist)
      }else if(this.$store.state.idx==3){
        this.detaillist=res.data.items[3].itemlist[this.$store.state.detailId];
         console.log(this.detaillist)
      }else if(this.$store.state.idx==4){
        this.detaillist=res.data.items[4].itemlist[this.$store.state.detailId];
         console.log(this.detaillist)
      }else if(this.$store.state.idx==5){
        this.detaillist=res.data.items[5].itemlist[this.$store.state.detailId];
      }else{
        return;        
      }
		    	this.collectNum=this.detaillist.collect;
			  
		    })
		    .catch(error => {
		      console.log(error);
		    })
		  },
		  computed:{
			idx(){
				var Id=this.$route.path.split('/').splice(2,1)+'';
    				this.$store.state.detailId=Id;
			}
		
	},
    methods:{
      attetion(){
        this.flag=!this.flag
        this.zanNum=parseInt(this.zanNum);
        if(this.flag){
          this.zanNum+=1
        }else{
          this.zanNum-=1
        }
      },
       open (position) {
        this.val = false 
        this.val1 = true
        this[position + 'Popup'] = true
      },
      close (position) {
        this.val = true
        this.val1 = false 
        this[position + 'Popup'] = true
      },
      collect(){
         this.cllect=!this.cllect
        this.collectNum=parseInt(this.collectNum);
        if(this.cllect){
          this.collectNum+=1
        }else{
          this.collectNum-=1
        }

      }
  }
  ,
 watch: {
    topPopup (val) {
      if (val) {
        setTimeout(() => {
          this.topPopup = false,
          this.topPopup2 = false
        },1000)
      }
    }
  }
	}
</script>
<style scoped lang="less">
.detaillist{
	width: 100%;
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
  	}
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
  	.detail_content{
  		padding-bottom: 56/50rem;
  		&>img{
  			width: 100%;
  		}
  		.userinfo{
  			padding:15/50rem;
  			overflow: hidden;
  			img{
  				float: left;
  			}
  			.user_icon{
  				width: 50/50rem;
  				height: 50/50rem;
  				border-radius: 50%;
  			}
  			.user{
  				float: left;
  				margin-left: 20/50rem;
  				margin-top: 20/50rem;
  			}
  			.attetion{
  				float: right;
		  				margin-top: 15/50rem;
  				border: 1px solid #535353;
  				padding:5/50rem;
  				color: #535353;
  				border-radius: 5/50rem;
  			}
        .changeattetion{
          border: 1px solid #FF6B9D;
          color: #FF6B9D;
        }

  		}
  		.detail{
  			color:#535353;
  			padding:25/50rem;
  			line-height: 24/50rem;
  			font-size: 18/50rem;
  		}
  		
  	}
.footer{
  			width: 100%;
  			position:fixed;
  			background: #fff;
  			bottom:0px;
  			left:0px;
  			p{
  				width: 33.3%;
  				float: left;
  				padding:20/50rem 0px;
  				box-sizing: border-box;
  				color:#404040;
  				
          .active{
              color:#FF6A9D;
          }
          .collectActive{
            color:#FF6A9D
          }
  			}

  		}
  	
</style>