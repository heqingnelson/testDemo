<template>
    <div id="app">
        <h2>Parent</h2>
        <h3>{{msg}}</h3>
        <child1 :title="title1" @getmsg="getmsg" :foo="foo" :boo="boo" :coo="coo" @getterss='getterss'></child1>
        <child2></child2>
    </div>
</template>

<script>
    import Child1 from '@/components/demo1/Child1';
    import Child2 from '@/components/demo1/Child2';
    export default {
        name: 'app',
        provide: {
            woniu: '我是骚气的大圣老师',
        },
        components: {
            Child1,
            Child2
        },
        data() {
            return {
                msg: '',
                title1: '我是你爸爸',
                foo: 'Javascript',
                boo: 'Html',
                coo: 'CSS',
                doo: 'Vue',
            };
        },
        methods: {
            getmsg(msg) {
                this.msg = msg;
            },
            getterss() {
                this.msg = 'sdsdssdsdsd';
            },
        },
        mounted() {
            this.$on('dispatch', msg => {
                this.msg = '接收dispatch消息:' + msg;
            });
            this.$bus.$on('event-bus', msg => {
                this.msg = '接收event-bus消息:' + msg;
            });
        },
    };
</script>
<style>
    div {
        border: 3px blue solid;
        padding: 10px;
        display: inline-block;
        vertical-align: top;
        /* width:50%; */
    }

    h1,
    h2 {
        font-size: 18px;
        margin: 5px 0;
    }

    h3 {
        color: red;
        font-size: 14px;
    }
</style>