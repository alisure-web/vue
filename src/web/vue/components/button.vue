<!--
    button 组件 说明：
        1.当点击按钮时，触发clickButton事件。
        2.可设置主题。
        3.可设置文字、大小。

    使用方法：
        1.导入组件
            import myButton from "./vue/button.vue"
            components: { myButton }
        2.设置组件
            <my-button theme="theme-2" text="按钮" height="32px"
                   width="64px" font-size="14px" @clickButton="myButtonClick"></my-button>
        3.响应点击事件
            methods: {
                myButtonClick: function () {
                    alert("点击了按钮");
                }
            }
-->

<style>
    .my-button{
        text-align: center;
        float: left;
        user-select: none;
        cursor: pointer;
    }

    .my-button.theme-1{
        background-color: #7f7f7f;
    }
    .my-button.theme-1:hover{
        background-color: cadetblue;
    }
    .my-button.theme-1:active{
        background-color: chartreuse;
    }

    .my-button.theme-2{
        background-color: #ead49d;
    }
    .my-button.theme-2:hover{
        background-color: #eacc71;
    }
    .my-button.theme-2:active{
        background-color: #eac43e;
    }
</style>

<template>
    <div class="my-button" :class="theme"
         :style="{'width':width, 'height':height, 'line-height':height,
         'border-radius':radius, 'font-size': fontSize}"
         @click.prevent="clickButton($event)"
    >
        {{text}}
    </div>
</template>

<script>
    export default {
        name: "myButton",
        data() {
            return {

            }
        },
        props: {
            text: {
                type: String,
                default: "按钮",
                required: true
            },
            width: {
                type: String,
                default: "32px"
            },
            height: {
                type: String,
                default: "64px"
            },
            radius: {
                type: String,
                default: "5px"
            },
            fontSize: {
                type: String,
                default: "14px"
            },
            theme: {
                type: String,
                default: "theme-1"
            }
        },
        methods: {
            clickButton: function (event) {
                this.$emit("clickButton");
            }
        }
    }
</script>