<template>
    <div class="headerTop">
        <div class="content">
            <div class="logo">
                <img src="./../assets/img/icon_logo_zhuo.png" alt="" />
            </div>
            <div class="tabbar">
                <div @click="changePath(1,'Home')">
                    <p>首页</p>
                    <span v-if="routerActive == 1"></span>
                </div>
                <div @click="changePath(2,'about')">
                    <p>关于卓越</p>
                    <span v-if="routerActive == 2"></span>
                </div>
                <div @click="changePath(3,'server')">
                    <p>行业经验</p>
                    <span v-if="routerActive == 3"></span>
                </div>
                <div @click="changePath(4,'member')">
                    <p>主要成员</p>
                    <span v-if="routerActive == 4"></span>
                </div>
                <div @click="changePath(5,'contact')">
                    <p>联系我们</p>
                    <span v-if="routerActive == 5"></span>
                </div>
                
            </div>
            <div class="changeLang" @click="showChange = !showChange">
                <img class="language" src="./../assets/img/icon_language_blue.png" alt="" />
                <img class="downward" src="./../assets/img/icon_downward_blue.png" alt="" />
            </div>
            <div class="changeBox" v-if="showChange">
                <div class="changeListc">
                    <span>选择您想阅读的语言</span>
                    <img class="error" @click="showChange=false" src="./../assets/img/icon_error_black.png" alt="" />
                </div>
                <div class="changeListc" :class="[active==0?'active':'']" @click="active=0">
                    <span>English</span>
                    <img class="yes" src="./../assets/img/icon_yes_white.png" alt="" />
                </div>
                <div class="changeListc" :class="[active==1?'active':'']" @click="active=1">
                    <span>中文</span>
                    <img class="yes" src="./../assets/img/icon_yes_white.png" alt="" />
                </div>


            </div>
        </div>
    </div>
</template>

<script>
    import lange from '../lang/zh-CN'
    export default {
        name: 'headerTop',
        props: {
            msg: String
        },
        data() {
            return {
                showChange: false,
                active: 0,
                routerActive: localStorage.getItem('routerIndex') || 1,
            }
        },
        watch: {
                
        },
        methods: {
            changePath(index, path) {

                this.$router.push({
                    name:path,
                })
                // console.log(index,'indexindex')
                localStorage.setItem('routerIndex', index)
                this.$nextTick(() => {
                    this.routerActive = index;
                })
                
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .headerTop {
        width: 100%;
        height: 64px;
        background: #0A1B2F;
    }

    .content {
        width: 1400px;
        height: 100%;
        margin: 0 auto;
        /* padding-top: 10px; */
        display: flex;
        position: relative;
    }

    .changeBox {
        position: absolute;
        right: 0;
        top: 56px;
        /* border: 1px solid ; */
    }

    .changeBox .changeListc {
        /* width: 270px; */
        height: 56px;
        /* background-color: #fff; */

        background: #fff;
        padding: 0 34px;
        display: flex;
        align-items: center;
        cursor: pointer;
        /* color: #ccc; */
        border: 1px solid #eee;
    }

    .changeBox .changeListc span {
        float: left;

        font-size: 17px;
        font-family: SourceHanSansSC, SourceHanSansSC;
        font-weight: 400;

        line-height: 25px;
    }

    .changeBox .changeListc .yes {
        display: block;
        height: 11px;
        width: 17px;
        float: right;
        margin-left: 33px;
    }

    .changeBox .changeListc .error {
        display: block;
        height: 17px;
        width: 17px;
        float: right;
        margin-left: 33px;
        color: #fff;
    }

    .changeBox .active {
        color: #fff;
        background: #022EA8 !important;
    }

    .changeBox .changeList {
        width: 270px;
        height: 56px;
        background-color: #030F1E;
        font-size: 17px;
        color: #0A1B2F;
    }

    .content .logo {
        width: 64px;
        height: 24px;
        margin-top: 15px;
    }

    .content .logo img {
        display: block;
        height: 100%;
        width: 100%;
    }

    .content .tabbar {
        /* width: 700px;
        height: 60px; */
        /* border-radius: 26px; */
        /* border: 1px solid #FFFFFF; */
        margin: 0 auto 0;
        /* padding: 0 175px; */
        text-align: center;
        line-height: 60px;
        color: #fff;
        height: 100%;
        display: flex;
        align-content: center;
        flex-wrap: wrap;
        cursor: pointer;
    }

    .content .tabbar div {
        margin: 0 25px;
        /* display: inline-block; */

        font-size: 16px;
    }

    .content .tabbar div p {
        line-height: 1;
        /* display: inherit; */
    }

    .content .tabbar div span {
        display: block;
        width: 17px;
        height: 2px;
        background: #022EA8;
        border-radius: 1px;
        margin: 0 auto;
        margin-top: 13px;
    }

    .content .changeLang {
        width: 56px;
        height: 34px;
        background: #E9E9E9;
        border-radius: 26px;
        /* line-height: 60px; */
        text-align: center;
        /* padding: 6px 10px; */
        /* margin-top: 10px; */
        padding: 0 10px;
        display: flex;
        align-items: center;
        justify-content: space-around;
        margin-top: 10px;
    }

    .content .changeLang .language {
        display: block;
        height: 16px;
        width: 16px;
        /* float: left; */
        margin-right: 10px;
    }

    .content .changeLang .downward {
        /* float: left; */
        display: block;
        width: 11px;
        height: 6px;
    }
</style>