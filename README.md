
总文件夹名称：overseashopping

进入app:一个启动页面（start.vue），3个轮播页面(slideshow.vue)（最后一张轮播点击进入登录页面）
登录界面（login.vue(1.jpg)）:登录功能，新人注册（reg）功能，忘记密码
（qq登录，微信登录，微博登录），登录完成进入homepage页面（默认index中（推荐（recommend.vue）））


<!-- 搜索功能 -->
<!-- https://suggest.taobao.com/sug?q=keyword&code=utf-8&area=c2c&nick=&sid=null -->
通过关键词：keyword
固定导航条（搜索框）搜索（功能：获取焦点：热门搜索与历史(8.jpg)）


<!-- 网络接口 -->

<!-- 数据通过axios请求数据 -->
在config文件中index.js写跨域请求的(修改后注意要重启服务器，本次共请求两个地址，写在这里，解决跨域问题)
'/api': {
            //目标：指向的网络地址
            target: 'http://data.allenamy.com',
            //webpack的属性，映射一个host
            changeOrigin: true,
            pathRewrite: {
                '^/api': ''
            }
        },
    '/url': {
        //目标：指向的网络地址
        target: 'https://suggest.taobao.com',
        //webpack的属性，映射一个host
        changeOrigin: true,
        pathRewrite: {
            '^/url': ''
        }
    }
通过地址栏获取动态id，通过判断id来取数据中下标为id的数据，在页面中显示
使用vuex数据共享的方式，多个页面共同使用

<!-- 安装的插件 -->
element:import { Tabs,  TabPane,Message,Button} from 'element-ui'

安装：cnpm i element-ui -S
	
	 npm i && npm i element-ui安装依赖

swiper:import VueAwesomeSwiper from 'vue-awesome-swiper'(轮播图)
		require('swiper/dist/css/swiper.css')
		Vue.use(VueAwesomeSwiper)
安装：cnpm install --save vue-awesome-swiper

<!-- 关注功能插件 -->

import MuseUI from 'muse-ui'
import 'muse-ui/dist/muse-ui.css'

弹出框：关注成功-取消关注
<mu-popup position="top" v-if="val1"  :overlay="false" popupClass="demo-popup-top" :open="topPopup">关注成功</mu-popup>
<mu-popup position="top" v-else="val1" :overlay="false" popupClass="demo-popup-top" :open="topPopup">取消关注</mu-popup>

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






页面主页（homepage.vue）:{

首页（index.vue）,
发现（find.vue），
购买（buy.vue）,
消息（message.vue）,
我（mine.vue）
}


首页（index）:{
推荐（recommend.vue）(2.jpg)->点击商品跳转详情页(goods-detail.vue)(3.jpg),
关注（attention.vue），
国家（nation.vue），
护肤（skincare.vue）,
时尚（fashion.vue），
彩妆（cosmetics.vue）
}

发现（find.vue）:{
求购信息(asktobuy.vue)->（图片来源，文件名称扁平中14.jpg）;
热门话题（hottopic.vue）->(图片来源，扁平中13.jpg);
走到哪购到哪（gowhere.vue）(11.jpg)->点击进入城市详情：东京（tokyo.vue）(10.jpg);


Muse-Ul
1.安装:npm install --save muse-ui

2.加载:
	import Vue from 'vue'
	import MuseUI from 'muse-ui'
	import 'muse-ui/dist/muse-ui.css'
	Vue.use(MuseUI)
3.组件加载:(在build中webpack.base.conf.js中加入)
	{
        test: /muse-ui.src.*?js$/,
        loader: 'babel'
      }
 4.main.js引入:
 	import 'muse-components/styles/base.less' // 加载基础的样式
	import appBar from 'muse-components/appBar'
	import avatar from 'muse-components/avatar'
	Vue.component(appBar.name, appBar)
	Vue.component(avatar.name, avatar)
	}
购买（buy.vue）:{
5张轮播图，8个图表导航，某些商品列表(9.jpg)
点击更多有一个跳转页面（更多：more.vue）(5.jpg).
彩妆图表点击进去跳转（goods.vue）(6.jpg),
下面商品列表点击跳转(goods-detail.vue)(4.jpg)
八个路由：{
buy文件夹{
components文件夹：Navshop.vue
pages:{
	pageslist:{
				}
	routerview{
	}
	accessories.vue(配饰)
	ChildMom.vue(母婴)
	clother.vue(服饰)
	goods.vue(商品){
	}
	health.vue(保健)
	househome.vue(家居)
	more.vue(更多)
	personcare.vue(个人护理)
}
}
}
}
消息（message.vue）:{
动态(dynamic.vue),
互动(interation.vue):(16.jpg),->互动详情（interracdetail.vue）
通知(inform.vue)
}
我（mine.vue）：{
我的分享（myshare.vue）:(17.jpg)
我的求购(myrequst.vue)
}
