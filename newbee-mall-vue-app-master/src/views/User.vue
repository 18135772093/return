<template>
  <div class="user-box">
    <s-header :name="'个人中心'"></s-header>
    <div class="user-info">
      <div class="info">
        <img src="//s.weituibao.com/1583583975067/user-graduate%20(1).png"/>
        <div class="user-desc">
          <span>昵称：{{ user.nickName }}</span>
          <span>登录名：{{ user.loginName }}</span>
          <span class="name">个性签名：{{ user.introduceSign }}</span>
        </div>
      </div>
    </div>
    <!--    <van-grid direction="horizontal" :column-num="2">-->
    <!--      <van-grid-item icon="photo-o" text="回收订单" />-->
    <!--      <van-grid-item icon="photo-o" text="文字" />-->
    <!--      <van-grid-item icon="photo-o" text="文字" />-->
    <!--    </van-grid>-->
    <!--    <ul class="user-list">-->
    <!--      <li @click="goTo('order')">-->
    <!--        <span>回收订单</span>-->
    <!--        <van-icon name="arrow" />-->
    <!--      </li>-->
    <!--      <li @click="goTo('setting')">-->
    <!--        <span>账号管理</span>-->
    <!--        <van-icon name="arrow" />-->
    <!--      </li>-->
    <!--      <li @click="goTo('address?from=mine')">-->
    <!--        <span>地址管理</span>-->
    <!--        <van-icon name="arrow" />-->
    <!--      </li>-->
    <!--      <li @click="goTo('about')">-->
    <!--        <span>关于我们</span>-->
    <!--        <van-icon name="arrow" />-->
    <!--      </li>-->
    <!--      <li @click="goTo('problem')">-->
    <!--        <span>常见问题</span>-->
    <!--        <van-icon name="arrow" />-->
    <!--      </li>-->
    <!--    </ul>-->
<!--    <div class="image">-->
<!--      <img src="../newbee-mall-vue-app-master/static-files/保护环境.png">-->
<!--    </div>-->
    <van-cell-group class="user-list">
      <van-cell title="回收订单"
                icon="records"
                is-link
                @click="goTo('order')"/>
      <van-cell title="账号管理"
                icon="gold-coin"
                @click="goTo('setting')"
                is-link/>
      <van-cell title="地址管理"
                icon="location"
                @click="goTo('address?from=mine')"
                is-link/>
      <van-cell title="关于我们"
                icon="contact"
                @click="goTo('about')"
                is-link/>
      <van-cell title="常见问题"
                icon="question"
                @click="goTo('about')"
                is-link/>
    </van-cell-group>
    <!--    <div class="use-often">常用功能-->
    <!--      <div class="address-edit" >地址管理</div>-->
    <!--      <div class="account-edit" >账号管理</div>-->
    <!--      <div class="about-us" >关于我们</div>-->
    <!--    </div>-->
    <nav-bar></nav-bar>
  </div>
</template>

<script>
  import navBar from '@/components/NavBar'
  import sHeader from '@/components/SimpleHeader'
  import {getUserInfo} from '../service/user'

  export default {
    components: {
      navBar,
      sHeader
    },
    data() {
      return {
        user: {}
      }
    },
    async mounted() {
      const {data} = await getUserInfo()
      this.user = data
    },
    methods: {
      goBack() {
        this.$router.go(-1)
      },
      goTo(r) {
        this.$router.push({path: r})
      }
    }
  }
</script>

<style lang="less" scoped>
  @import '../common/style/mixin';

  .user-box {
    .user-header {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 10000;
      .fj();
      .wh(100%, 44px);
      line-height: 44px;
      padding: 0 10px;
      .boxSizing();
      color: #252525;
      background: #fff;
      border-bottom: 1px solid #dcdcdc;

      .user-name {
        font-size: 14px;
      }
    }

    .user-info {
      width: 94%;
      margin: 10px;
      height: 115px;
      background: linear-gradient(90deg, @primary, #51c7c7);
      box-shadow: 0 2px 5px #269090;
      border-radius: 6px;
      margin-top: 50px;

      .info {
        position: relative;
        display: flex;
        width: 100%;
        height: 100%;
        padding: 25px 20px;
        .boxSizing();


        .user-desc {
          display: flex;
          flex-direction: column;
          margin-left: 10px;
          line-height: 20px;
          font-size: 14px;
          color: #fff;

          span {
            color: #fff;
            font-size: 14px;
            padding: 2px 0;
          }
        }

        .account-setting {
          position: absolute;
          top: 10px;
          right: 20px;
          font-size: 13px;
          color: #fff;

          .van-icon-setting-o {
            font-size: 16px;
            vertical-align: -3px;
            margin-right: 4px;
          }
        }
      }
    }
    .image{
      padding: 10px 5px;
      margin-top: 30px;
    }

    .user-list {
      padding: 10px 5px;
      margin-top: 120px;

      li {
        height: 40px;
        line-height: 40px;
        border-bottom: 1px solid #e9e9e9;
        display: flex;
        justify-content: space-between;
        font-size: 14px;
        padding-left: 20px; /* 设置字体向右移动20px，否者会遮挡到背景图片 */

        .van-icon-arrow {
          margin-top: 13px;
        }
      }
    }

    /*use-often{*/
    /*  width: 100%;*/
    /*  height: 64px;*/
    /*  display: flex;*/
    /*}*/
    /*address-edit{*/
    /*  width: 33%;*/
    /*  height: 50px;*/

    /*}*/
    /*account-edit{*/
    /*  width: 33%;*/
    /*  height: 50px;*/

    /*}*/
    /*about-us{*/
    /*  width: 33%;*/
    /*  height: 50px;*/
    /*}*/
  }
</style>
