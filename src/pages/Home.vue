<template>
    <StickyLayout :isShowSideBar.sync="isShowSideBar">
        
        <!-- 侧边菜单 -->
        <template slot="side-bar">
            
        </template>
        <!-- 头部 -->
        <FlexBox slot="header" class="header">
            <Icon value="bars" @click.native="showSideBar"></Icon>
            <FlexItem>
                <img class="logo" src="../assets/logo.png">
            </FlexItem>
            <Icon value="search"></Icon>
        </FlexBox>

        <!-- 主体 -->
        <transition name="fade-left" mode="out-in">
            <router-view></router-view>
        </transition>

        <!-- 底部 -->
        <FlexBox slot="footer" class="footer">
            <FlexItem>
                <router-link tag="span" to="/home/index" class="button">
                    <Icon value="home"></Icon>
                    <p>home</p>
                </router-link>
            </FlexItem>
            <FlexItem>
                <router-link tag="span" to="/home/presale" class="button">
                    <Icon value="clock-o"></Icon>
                    <p>presale</p>
                </router-link>
            </FlexItem>
            <FlexItem>
                <router-link tag="span" to="/home/category" class="button">
                    <Icon value="compass"></Icon>
                    <p>find</p>
                </router-link>
            </FlexItem>
            <FlexItem>
                <router-link tag="span" to="/home/shop-cart" class="button">
                    <Icon value="shopping-bag"></Icon>
                    <p>cart</p>
                </router-link>
            </FlexItem>
            <FlexItem>
                <router-link tag="span" to="/home/my" class="button">
                    <Icon value="user-circle-o"></Icon>
                    <p>my</p>
                </router-link>
            </FlexItem>
        </FlexBox>
    </StickyLayout>
</template>
<script>
import StickyLayout from '@/packages/layout/Sticky';
import SideBar from '@/packages/SideBar/SideBar';

export default {
    name: 'Home',

    data() {
        return {
            isShowSideBar: true
        }
    },

    methods: {
        showSideBar(){
            this.isShowSideBar = true;
        }
    },

    components: {
        StickyLayout
    }
}
</script>
<style scoped lang="scss">
@import '../scss/theme.scss';
.container {
    height: 100%;
    width: 100%;
    position: relative;

    .header{box-shadow: $shadowDown;padding:10px 15px;background: #fff;
        i{font-size: 20px;}
        .logo{text-align: center;display: table;margin:auto;height: 20px;}
    }

    .footer {
        box-shadow: $shadowUp;
        .button {
            color: $dark;
            position: relative;
            padding: $gutter / 2;
            display: block;
            background: #fff;
            text-align: center;
            font-size: 24px;
            transition: all .3s;
            &.active {
                background: $light;
            }
            &:active {
                background: $light;
            }
        }
        .router-link-active{background: $light;}
    }
}
</style>
