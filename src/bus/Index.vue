<template>
    <van-list
            v-model="loading"
            :finished="finished"
            finished-text="没有更多了"
            @load="onLoad"
            offset="150"
    >
        <van-cell v-for="item in list" :key="item.id" :title="item.number" @click="infoClick(item.id)"/>
    </van-list>
</template>

<script>
    import Vue from 'vue';
    import {Form, Button, Field, List, Cell} from 'vant';

    Vue.use(Form);
    Vue.use(Button);
    Vue.use(Field);
    Vue.use(List);
    Vue.use(Cell);
    export default {
        data() {
            return {
                list: [],
                loading: false,
                finished: false,
                pageNo: 1,
            };
        },
        methods: {
            onLoad() {
                this.axios.get("http://busapi.cyanzoy.top/bus/getBusInfo/?pageSize=10&pageNo="+this.pageNo+"").then(
                    (res) => {
                        if(res.data.data.pageNo == 0){
                            this.finished = true
                        }
                        res.data.data.list.forEach((e) => {
                            this.list.push(e)
                        })
                        this.pageNo++
                        console.log(this.pageNo)
                        console.log(res.data.data.list)
                        // 加载状态结束
                        this.loading = false;
                    }
                ).catch((response) => {
                    console.log(response);
                })
                // 异步更新数据
                // setTimeout 仅做示例，真实场景中一般为 ajax 请求
                // setTimeout(() => {
                //     for (let i = 0; i < 15; i++) {
                //         this.list.push(this.list.length + 1);
                //     }
                //
                //     // 加载状态结束
                //     this.loading = false;
                //
                //     // 数据全部加载完成
                //     if (this.list.length >= 40) {
                //         this.finished = true;
                //     }
                // }, 2000);
            },
            infoClick(e) {
                console.log(e)
            }
        },
    };
</script>