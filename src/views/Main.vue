<template>
  <div class="main">
    <div class="main_head">
      <span class="head_left">
        北京
      </span>
      <span class="head_center">
        <van-search
          placeholder="请输入搜索关键词"
          shape="round"
          background="#ffbf00"
        >
        </van-search>
      </span>
      <span class="head_right">
        用户
      </span>
    </div>
    <div class="main_nav">
     <dl v-for="(item,index) in data1" :key="index" @click="jump()">
       <dt><img :src="item.img"></dt>
       <dd>{{item.name}}</dd>
     </dl>
    </div>
    <div class="main_body">
      <p class="youlike">猜你喜欢</p>
      <div class="box"  v-for="(item,index) in data2" :key="index">
        <dl>
          <dt><img :src="item.img" class="data2_img"></dt>
          <dd class="data2_name">{{item.name}}</dd>
          <dd class="data2_con">
            [{{item.con}}]
            {{item.message}}
          </dd>
          <dd class="data2_price">
          <span class="col">{{item.price}}元</span>
          <span class="old_price">门市价:{{item.oldprice}}元</span>
          <span class="num">已售{{item.num}}</span>
          </dd>
        </dl>
      </div>
      
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data1:[],
      data2:[],
    };
  },
  created(){
    this.axios.get("data1.json").then((res)=>{
      this.data1 = res.data
      // console.log(res.data)
    })
    this.axios.get("data2.json").then((res)=>{
      this.data2 = res.data
      console.log(res.data)
    })
  },methods:{
    jump(){
      this.$router.push("./Home")
    }
  }
};
</script>

<style scoped>
.main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  background: #F0EFED;
}
.main_head {
  display: flex;
  width: 100%;
  height: 3.375rem;
  background: #ffbf00;
}
.main_nav {
  width: 100%;
  height: 10rem;
  background: white;
}
.main_body {
  flex: 1;
  overflow: auto;
  margin-top: 10px;
  background: white;
}
.head_left,
.head_right {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 3.125rem;
  height: 100%;
  /* background: purple; */
}
.head_center {
  flex: 1;
}
.main_nav dl{
  width: 20%;
  height: 50%;
  float: left;
  /* background: red; */
  text-align: center;
  padding-top:5px; 
}
dl,dd{
  padding: 0;
  margin: 0;
}
p{
  padding: 0;
  margin: 0;
}
.youlike{
  width: 100%;
  height: 1.875rem;
  line-height: 1.875rem;
  padding-left: 10px;
  box-sizing: border-box;
}
.data2_img{
  width:90px;
  height: 90px;
  padding: 6px;
  float: left;
}
.data2_name{
  width: 60%;
  margin-top: 10px;
  float: left;
}
.data2_con{
  width: 60%;
  margin-top: 10px;
  float: left;
  font-size: 12px;
}
.data2_price{
  width: 65%;
  margin-top: 20px;
  float: left;
}
.col{
  color: #FF6600;
}
.old_price{
  font-size: 12px;
  padding-left: 5px;
}
.num{
  float: right;
  font-size: 12px;
}
.box{
  width: 100%;
  height: 100px;
  float: left;
}
</style>
