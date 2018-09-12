<template>
    <div>
        <div class="header">
            <!-- 搜索栏 -->
            <icon type="search" size="16"></icon>
            <input type="text" placeholder="搜索">
        </div>
        <!-- 轮播图 -->
        <swiper indicator-dots autoplay circular>
            <swiper-item v-for="(item, index) in swiperList" :key="item.name">
                <image mode="aspectFill" :src="item.image_src"></image>
            </swiper-item>
        </swiper>
    </div>
</template>

<script>
import tool from '../../utils/index'
console.log(tool);
export default {
  data() {
    return {
        swiperList:[]//轮播图
    };
  },
  created() {
    //   获取轮播图数据
    tool.thenAjax({
        url:'api/public/v1/home/swiperdata'
    }).then(res=>{
        console.log(res);
        this.swiperList = res.data.message
    })
  }
};
</script>

<style lang="less" scoped>
    .header{
        padding: 20rpx 16rpx;
        position: relative;
        background-color: #ff2d4a;
        icon{
            position: absolute;
            top:34rpx;
            left: 50%;
            transform: translateX(-200%);
            z-index: 998;
        }
        input{
            height: 60rpx;
            border-radius: 10rpx;
            background-color: #fff;
            width: 100%;
            color:#bbb;
            text-align:center;
            font-size:24rpx;
        }
    }
    // 轮播图
    swiper{
        height: 340rpx;
        swiper-item{
            image{
                display: block;
                width: 100%;
                height: 100%;
            }
        }
    }
</style>
