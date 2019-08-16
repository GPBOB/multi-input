<template>
  <div id="app">
    <!--    新增-->
    <vueMultiInput :multiColumns="multiCol" @getMultiData="getResult"></vueMultiInput>
    <!--    编辑-->
    <!--    <vueMultiInput :e-multi-columns="multiCol" :e-multi-result="eMultiResult" @getMultiData="getResult" :is-add="false"></vueMultiInput>-->
  </div>
</template>

<script>
    import vueMultiInput from './MultiInput'

    export default {
        name: 'app',
        data() {
            return {
                multiCol: [
                    {
                        title: '树（材）种',
                        type: 'input_text',
                        key: "tree"
                    },
                    {
                        title: '树222',
                        type: 'input_text',
                        key: "trees"
                    }
                ],
                eMultiResult: [
                    {
                        tree: "333",
                        trees: "fgfdf"
                    },
                    {
                        tree: "333",
                        trees: "fgfdf"
                    },
                ]
            }
        },
        components: {
            vueMultiInput
        },
        methods: {
            //获取结果
            getResult(val) {
                console.log(val)
            }
        }
    }
</script>

<style>
</style>
