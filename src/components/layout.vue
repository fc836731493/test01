<template>
  <div class="index-wrap">
     <div class="index-left">
        <div class="index-left-block">
          <h2>全部产品</h2>
          <h3 v-for="(title,index) in productList" :key="index">
             {{ title.category }}
             <ul>
                <li v-for="(item,index) in title.list" :key="index">
                   {{ item.name }}
                   <span class="hot-tag" v-show="item.hot">HOT</span>
                </li>
             </ul>
             <div class="hr"></div>
          </h3>
        </div>
        <div class="index-left-block">
          <h2>经典电影排行版</h2>
        </div>
     </div>
     <div class="index-right">
        <div class="swiper-size">
          <swiper :options="swiperOption" >
            <swiper-slide>
                <a target="_blank" href="http://www.xiaohuar.com/p-1-2104.html">
                  <img class="swiperimg" src="../assets/slideShow/j1.jpg" alt="">
                </a>
            </swiper-slide>
            <swiper-slide>
                <a target="_blank" href="http://www.xiaohuar.com/p-1-2103.html">
                  <img class="swiperimg" src="../assets/slideShow/j2.jpg" alt="">
                </a>
            </swiper-slide>
            <swiper-slide>
                <a target="_blank" href="http://www.xiaohuar.com/p-1-2087.html">
                  <img class="swiperimg" src="../assets/slideShow/j3.jpg" alt="">
                </a>
            </swiper-slide>
            <swiper-slide>
                <a target="_blank" href="http://www.xiaohuar.com/p-1-2083.html">
                  <img class="swiperimg" src="../assets/slideShow/j4.jpg" alt="">
                </a>
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
            <div class="swiper-button-prev" slot="button-prev"></div>
            <div class="swiper-button-next" slot="button-next"></div>
          </swiper>
        </div>
        
     </div>
  </div>
</template>

<script>
export default {
  name: 'layout',
  data () {
    return {
      productList:[
        {
          category:"手机应用类",
          list:[
            {
              name:"91助手",
              url:"https://www.baidu.com/",
              hot:false
            },
            {
              name:"豌豆荚",
              url:"https://www.baidu.com/",
              hot:true
            },
            {
              name:"金山毒霸",
              url:"https://www.baidu.com/",
              hot:false
            }
          ]
        },
        {
          category:"PC产品类",
          list:[
            {
              name:"webstorm",
              url:"https://www.baidu.com/",
              hot:true
            },
            {
              name:"sublime",
              url:"https://www.baidu.com/",
              hot:false
            },
            {
              name:"hbuild",
              url:"https://www.baidu.com/",
              hot:false
            },
            {
              name:"atom",
              url:"https://www.baidu.com/",
              hot:false
            }
          ]
        }
      ],
      swiperOption: {
          pagination: {
            el: '.swiper-pagination',
          },
          loop:true,
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
          }
     },
     imgList:[
       {
         url:"../assets/slideShow/j1.jpg",
         target:"http://www.xiaohuar.com/p-1-2104.html"
       },
        {
         url:"../assets/slideShow/j2.jpg",
         target:"http://www.xiaohuar.com/p-1-2103.html"
       },
        {
         url:"../assets/slideShow/j3.jpg",
         target:"http://www.xiaohuar.com/p-1-2087.html"
       },
        {
         url:"../assets/slideShow/j4.jpg",
         target:"http://www.xiaohuar.com/p-1-2083.html"
       }
     ]
    }
  },
  created(){
    var url = this.HOST +'/musicBroadcasting';
    var qs=require('qs');
    this.$axios.get(url,{
      params:{
        count:10
      }
    })
    .then(res => {
      console.log(res);
    })
    .catch(error => {
      console.log(error);
    })
  }
}
</script>

<style scoped>
.index-wrap {
    width: 1200px;
    margin: 0 auto;
    overflow: hidden;
}
.index-left {
    float: left;
    width: 300px;
    text-align: left;
}
.index-right {
    float: left;
    width: 900px;
}
.index-left-block {
    margin: 15px;
    background: #fff;
    box-shadow:0 0 1px #ddd;
    height: 350px;
}
.index-left-block .hr {
    margin-bottom: 20px;
    height: 1px;
    width: 100%;
    background: #ddd;
}
.index-left-block h2 {
    background: #4fc08d;
    color:#fff;
    padding: 10px 15px;
    margin-bottom: 20px;
}
.index-left-block h3 {
    padding: 0 15px 5px 15px;
    font-weight: bold;
    color: #222;
}
.index-left-block ul {
    padding: 10px 15px;
}
.index-left-block li {
    font-weight: normal;
    padding: 5px;
}
.index-board-list {
    overflow: hidden;
    margin-top: 15px;
}
.index-board-item {
    float: left;
    width: 400px;
    background: #fff;
    box-shadow: 0 0 1px #ddd;
    padding: 20px;
    margin-right: 20px;
    margin-bottom: 20px;
}
.index-board-item-inner {
    min-height: 125px;
    padding-left: 120px;
}
.index-board-car .index-board-item-inner {
    background: url(../assets/images/1.png) no-repeat;
}
.index-board-loud .index-board-item-inner {
    background: url(../assets/images/2.png) no-repeat;
}
.index-board-earth .index-board-item-inner {
    background: url(../assets/images/3.png) no-repeat;    
}
.index-board-hill .index-board-item-inner {
    background: url(../assets/images/4.png) no-repeat;    
}
.index-board-item h2 {
    font-size: 18px;
    font-weight: bold;
    color: #000;
    margin-bottom: 15px;
}
.line-last {
    margin-right: 0;
}
.index-board-button {
    margin-top: 20px;
}
.lastest-news {
    min-height: 350px;
}
.hot-tag {
    background: red;
    color: #fff;
}
.new-item {
    display: inline-block;
    width: 230px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}

.swiper-size {
    margin-top: 15px;
    height: 400px;
}
.swiperimg {
    width:100%;
    height: 370px;
}
.button {
    color: #fff;
    background: #4fc08d;
    padding: 10px 20px;
    display: inline-block;
    cursor: pointer;
}
</style>
