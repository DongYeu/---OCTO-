<template>
  <div class="home">
    <img src="//s1.meituan.net/bs/file?f=meis/meishi.mobile:img/app_download_banner.png@5b5269e" class="home_img">
    <div class="home_head">
      <span class="head_left"><van-icon name="arrow-left" /></span>
      <span class="head_center">
        <van-search
          placeholder="输入商家名、品类或商圈"
          shape="round"
          background="#EBECED"
        >
        </van-search>
      </span>
      <span  class="head_right"><van-icon name="contact" /></span>
    </div>
    <div class="home_nav">
      <dl v-for="(item,index) in data" :key="index">
        <dt><img :src="item.img" class="nav_img"></dt>
        <dd>{{item.name}}</dd>
      </dl>
    </div>
    <div class="home_body">
      <div class="list">
        <van-dropdown-menu>
          <van-dropdown-item v-model="value1" :options="option1" />
          <van-dropdown-item v-model="value2" :options="option2" />
          <van-dropdown-item v-model="value3" :options="option3" />
          <van-dropdown-item v-model="value4" :options="option4"/>
        </van-dropdown-menu>
      </div>
      <div class="body_box" v-for="(item,index) in food" :key="index">
        <dl>
          <dt><img :src="item.img" class="food_img"></dt>
          <dd class="dd_name">{{item.name}}</dd>
          <dd class="dd_price">
            <van-rate v-model="item.star" size="10" />
            <span class="price">￥{{item.price}}/人</span>
            <span class="add">上地<{{item.dis}}</span>
          </dd>
          <dd class="con">
            <span class="con1">{{item.foodname}}</span>
            <span class="con2">{{item.num}}</span>
          </dd>
          <dd class="go">
            {{item.all}}
          </dd>
        </dl>
        <p class="p1">
          <span class="p_img">团</span>
          <span>
            {{item.two}}
          </span>
        </p>
        <p class="p2">
          <span class="p_img">减</span>
          <span>{{item.red}}</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      value1: 0,
      value2: 'a',
      value3: 'a',
      value4: 'a',
      data:[],
      food:[],
      option1: [
        { text: '全部商品', value: 0 },
        { text: '新款商品', value: 1 },
        { text: '活动商品', value: 2 }
      ],
      option2: [
        { text: '附近商家', value: 'a' },
        { text: '好评排序', value: 'b' },
        { text: '销量排序', value: 'c' },
      ],
      option3: [
        { text: '智能排序', value: 'a' },
        { text: '好评排序', value: 'b' },
        { text: '销量排序', value: 'c' },
      ],
      option4: [
        { text: '筛选', value: 'a' },
        { text: '好评排序', value: 'b' },
      ]
    }
  },
  created(){
    this.axios.get("data3.json").then((res)=>{
      this.data = res.data
      // console.log(res.data)
    })
    this.axios.get("data4.json").then((res)=>{
      this.food = res.data
      console.log(res.data)
    })
  }
}
</script>

<style scoped>
dl,dd{
  padding: 0;
  margin: 0;
}
.home{
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  background: #F0F0F0;
  overflow: auto;
}
.home_nav{
  width: 100%;
  height: 10rem;
  background: #ffffff;
  margin-bottom: 10px;
}
.home_nav dl{
  width:25%;
  height: 45%;
  float: left;
  /* background: blue; */
  text-align: center;
}
.nav_img{
  margin-top: 10px;
}
.home_head{
  display: flex;
  width: 100%;
  height: 54px;
  position: fixed;
  z-index: 999;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
}
.head_left,.head_right{
  line-height: 50px;
  text-align: center;
  width: 50px;
  height: 100%;
  background: #EBECED;
}
.head_center{
  flex: 1;
}
.home_body{
  flex: 1;
  overflow: auto;
  background: white;
}
.list{
  width: 100%;
  height: 50px;
  /* background: pink; */
}
.body_box{
  width: 100%;
  height: 200px;
  /* background: yellow; */
}
.food_img{
  width:100px;
  height: 100px;
  float: left;
  padding: 10px;
}
.dd_name{
  width: 60%;
  float: left;
  margin-top: 10px;
  margin-bottom: 5px;
}
.con1{
  padding-right: 5px;
}
.con2{
  color: #C1A254;
  background: #FBF4E4;
}
.price{
  font-size: 12px;
}
.add{
  float: right;
  font-size: 12px;
  margin-right: 10px;
}
.con{
  width: 60%;
  float: left;
  font-size: 12px;
  margin-top: 5px;
}
.go{
  width: 65%;
  float: left;
  font-size: 12px;
  color: #38C2AA;
  margin-top: 15px;
}
.p1,.p2{
  width: 100%;
  height: 30px;
  background: white;
  float: left;
  line-height: 30px;
  padding-left: 120px;
  box-sizing: border-box;
}
p{
  margin: 0;
  padding: 0;
}
.p_img{
  display: inline-block;
  width: 20px;
  height: 20px;
  background: #5CB0CB;
  font-size: 15px;
  text-align: center;
  line-height: 20px;
  color: white;
}
.home_img{
  width: 100%;
  height: 100px;
}
</style>