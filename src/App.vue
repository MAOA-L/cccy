<template>
    <div id="app">
        <van-nav-bar
                title="标题"
                left-text="返回"
                right-text="按钮"
                left-arrow
                @click-left="onClickLeft"
                @click-right="onClickRight"
        />
<!--        <div id="nav">-->
<!--            &lt;!&ndash;      <router-link to="/">Home</router-link> |&ndash;&gt;-->
<!--            &lt;!&ndash;      <router-link to="/about">About</router-link>&ndash;&gt;-->
<!--            &lt;!&ndash;      <router-link to="/bus">BBBus</router-link>&ndash;&gt;-->
<!--        </div>-->
        <router-view/>
    </div>
</template>
<script>
    import Vue from 'vue';
    import {NavBar, Toast} from 'vant';

    Vue.use(NavBar);
    Vue.use(Toast);

    export default {
        methods: {
            onClickLeft() {
                Toast('返回');
            },
            onClickRight() {
                Toast('按钮');
            },
        },
    };
</script>
<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    #nav {
        padding: 30px;
    }

    #nav a {
        font-weight: bold;
        color: #2c3e50;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }
</style>
