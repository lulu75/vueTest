<template>
  <div style="width: 100%; height: 100%;" id="app" @click="cityShow(1)">
    <!-- 顶部搜索 -->
    <div style="margin: auto;width: 1200px;">
      <div style="margin: 30px 0px;display: flex;">
        <span><img src="../../static/image/logo.png" /></span>
        <div class="city_div">
          <span class="address_lab_title" @click.stop="cityShow(2)">{{selectCity}}<img /></span>
          <div class="city_select" v-if="city_show">
            <!-- 填充数据  list为数据源-->
            <span class="item_city" v-bind:key='index' v-for="(item,index) in list" :class="{'item_city_select':showclass==index}"
              v-on:click="show(index,item)">{{item.name}}</span>
          </div>
        </div>
        <div class="searchbgdiv">
          <div class="searchtypediv">
            <span class="searchtype" @click.stop="showsarchtype">
              {{searchType}}
            </span>

            <ul v-if="sarchTypeshow">
              <li @click="searchtypeClick('作品')">作品</li>
              <li @click="searchtypeClick('设计师')">设计师</li>
              <li @click="searchtypeClick('楼盘')">楼盘</li>
              <li @click="searchtypeClick('装修百科')">装修百科</li>
            </ul>
          </div>
          <img class="searchtypeimg" src="../../static/image/icdown.png" v-if="icdownshow" />
          <img class="searchtypeimg" src="../../static/image/icup.png" v-if="icupshow" />
          <input style="border: none;outline: none;width: 400px;" placeholder="请输入搜索关键字" />
          <span style="background: #a01313;color: #fff;display: block;width: 70px;float: right;text-align: center;">搜索</span>


        </div>
        <span style="padding: 0px 25px;margin: 8px 10px;">
          <img src="../../static/image/call.jpg" style="margin-top: 8px; display: block; float: left;" />
          <span style="display: block; float: left; line-height: 42px; margin:0 10px">135452544525</span>
        </span>
      </div>
      <div class="home_type_div">
        <span class="type_all">所有分类</span>
        <span style="color:#A01313">首页</span>
        <span>锦华</span>
        <span>案例</span>
        <span>楼盘</span>
        <span>设计师</span>
        <span>视频</span>
        <span>百科</span>
        <span>装修报价</span>
        <!-- 所有分类 -->
        <div class="banner_filter">
          <div class="loupan_title"><span>装修楼盘</span></div>
          <div class="loupan_list">
            <span v-for="(item,index) in quyudata" :key="index">{{item.name}}</span>
            <div style="clear: both;"></div>
          </div>
        </div>
        <!-- 所有分类end -->
      </div>
    </div>
    <!-- 顶部搜索end -->
    <!-- 轮播图 -->
    <div class="banner_div" style="position: relative;">
      <mt-swipe :auto="4000" >
        <mt-swipe-item><img src="../../static/image/banner1.jpg" /></mt-swipe-item>
        <mt-swipe-item><img src="../../static/image/banner2.jpg" /></mt-swipe-item>
        <mt-swipe-item><img src="../../static/image/banner3.jpg" /></mt-swipe-item>
      </mt-swipe>
<div class="banner_filter_div" style="width: 1200px;background: #007AFF; position: relative;margin: 0 auto;height: 200px;"></div>

    </div>
  </div>
</template>

<script>
  export default {

    data() {
      return {
        showclass: 0,
        selectCity: "南京",
        list: [{
          name: "南京",
          id: 1
        }, {
          name: "杭州",
          id: 2
        }, {
          name: "上海",
          id: 3
        }, {
          name: "浙江",
          id: 2
        }],
        city_show: false,
        searchType: "作品",
        sarchTypeshow: false,
        icdownshow: true,
        icupshow: false,
        quyudata: [{
            name: "观山湖区",
            id: "1"
          }, {
            name: "云岩区",
            id: "2"
          }, {
            name: "花溪区",
            id: "3"
          }, {
            name: "乌当区",
            id: "2"
          }, {
            name: "白云区",
            id: "2"
          }, {
            name: "南明区",
            id: "2"
          }, {
            name: "清镇市",
            id: "2"
          }, {
            name: "开阳县",
            id: "2"
          },
          {
            name: "息烽县",
            id: "2"
          }, {
            name: "修文县",
            id: "2"
          },
        ],

      }
    },
    methods: {
      show(status, item) {
        this.showclass = status;
        this.selectCity = item.name;
      },
      // 城市选择点击
      cityShow(isshow) {
        if (isshow == 1) {
          this.city_show = false;
        } else {
          if (this.city_show) {
            this.city_show = false;
          } else {
            this.city_show = true;
          }
        }

      },
      showsarchtype(status) {
        if (status == 1) {
          this.sarchTypeshow = false;
          this.icdownshow = true;
          this.icupshow = false;
        } else {
          if (this.sarchTypeshow) {
            this.sarchTypeshow = false;
            this.icdownshow = true;
            this.icupshow = false;
          } else {
            this.sarchTypeshow = true;
            this.icdownshow = false;
            this.icupshow = true;
          }
        }

      },
      searchtypeClick(type) {
        this.searchType = type;
      }
    }
  }
</script>

<style>
  .title_search {
    height: 90px;
    width: 1200px;
    background: #ffff00;
    margin: 0 auto;
  }

  .title_login {}

  .home_type_div {
    display: flex;
    position: relative;
  }

  .city_div {
    position: relative;
  }

  .city_select {
    width: 500px;
    position: absolute;
    margin-top: 0px;
    border: #ccc solid 1px;
    margin-left: 8px;
    background: #FFFFFF;
  }

  .city_select span {
    display: block;
    padding: 2px 10px;
    margin: 10px;
    float: left;
  }

  .home_type_div span {
    display: block;
    line-height: 40px;
    width: 90px;
    text-align: center;
    color: #000;

  }

  .item_city_select {
    background: #a01313;
    color: #fff;
  }

  .address_lab_title {
    line-height: 30px;
    background: #a01313;
    height: 30px;
    color: #fff;
    padding: 0px 25px;
    margin: 8px 10px;
    display: block;

  }



  .type_all {
    width: 200px !important;
    background: #A01313 !important;
    color: #FFFFFF !important;
    display: block;
    font-size: 16px;
    line-height: 40px;
    text-align: center;
  }


  .searchtype {
    width: 75px;
    line-height: 35px;
    font-size: 14px;
    color: #999999 !important;
    display: block;
    text-align: center;
  }

  .searchbgdiv {
    display: flex;
    border: 2px solid #a01313;
    height: 35px;
    line-height: 35px;
    margin-top: 6px;
    margin-left: 60px;

  }



  .searchtypeimg {
    width: 20px;
    height: 20px;
    margin-top: 8px;
    margin-right: 5px;
  }

  .searchtypediv ul {
    position: absolute;
    margin-top: 0px;
    margin-left: 0px;
    width: 85px;
    padding: 0px;
    margin-left: -2px;
    border: solid #A01313 2px;
    margin-top: 0px;
    background: #FFFFFF;
    border-top: solid #FFFFFF 0px;

  }

  .searchtypediv li {
    width: 85px;
    color: #999999;
    list-style: none;
    font-size: 14px;
    margin-left: 18px;
  }

  .searchtypediv {
    position: relative;
  }

  .banner_div {
    width: 100%;
    height: 420px;
    position: relative;

  }

  .banner_filter {
    width: 200px;
    height: 420px;
    position: absolute;
    top: 40px;
    background: rgba(0, 0, 0, 0.8);
    z-index: 2;
  }

  .loupan_title span {
    color: #969696 !important;
    font-size: 14px;
    line-height: 30px !important;
  }

  .loupan_list {padding: 0px 10px;}

  .loupan_list span {
    color: #FFFFFF;
    font-size: 12px;
    width: 60px;
    float: left;
    line-height: 30px;
  }
</style>
