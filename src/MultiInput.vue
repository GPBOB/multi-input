<template>
  <div class="multi_container">
    <div class="multi_input_con" v-for="count in mulNumber" v-if="mulNumber!=''" :key="count">
      <!--      新增板块-->
      <div class="multi_input_li" v-for="(item,index) in multiColumns" v-if="isAdd==true" :key="index">
        <span class="multi_input_li_title">{{item.title}}</span>
        <input v-if="item.type=='input_text'" type="text"
               v-model="multiResult[count-1][item.key]" :placeholder="item.placeholder"/>
        <span class="multi_input_li_unit" v-if="item.unit">{{item.unit}}</span>
      </div>
      <!--      编辑板块-->
      <div class="multi_input_li" v-for="(item,index) in eMultiColumns" v-if="isAdd==false" :key="index">
        <span class="multi_input_li_title">{{item.title}}</span>
        <input v-if="item.type=='input_text'" type="text"
               v-model="multiResult[count-1][item.key]" :placeholder="item.placeholder"/>
        <span class="multi_input_li_unit" v-if="item.unit">{{item.unit}}</span>
      </div>
      <img class="multi_img" src="./assets/yjcz_ico_jx2.png" alt="新增" v-show="count==mulNumber" @click="addInput">
      <img class="multi_img" src="./assets/yjcz_ico_jx1.png" alt="减少" v-show="count<mulNumber"
           @click="reduceInput(count-1)">
    </div>
  </div>
</template>

<script>
    export default {
        name: 'MultiInput',
        data() {
            return {
                mulNumber: 1,
                multiResult: [{}]//结果存储
            }
        },
        props: {
            //输入框数量
            mulNum: {
                type: Number,
                default: function () {
                    return 1
                }
            },
            /*
            *title：标题
            * type：输入框类型
            * key:字段名
            * unit:单位
             */
            multiColumns: {
                type: Array,
                default: function () {
                    return []
                }
            },
            //编辑获取的内容
            eMultiColumns: {
                type: Array,
                default: function () {
                    return []
                }
            },
            //存储编辑已存在的数据
            eMultiResult: {
                type: Array,
                default: function () {
                    return []
                }
            },
            //是否是新增模块（区分新增和编辑功能）
            isAdd: {
                type: Boolean,
                default: true
            },
        },
        methods: {
            //新增选择框
            addInput() {
                let multiColumnsObj = {}
                this.multiResult.push(multiColumnsObj)
                this.mulNumber++
            },
            //删除选择框
            reduceInput(num) {
                this.mulNumber--
                this.multiResult.splice(num, 1)
            }

        },
        watch: {
            //监听结果，传值给父组件
            multiResult: {
                handler:function(newVal, oldVal) {
                    this.$emit("getMultiData", this.multiResult)
                },
                deep:true
            },
            //编辑选择框，赋值
            // eMultiColumns(val) {
            //     let that = this
            //     if (val.length > 0) {
            //         that.multiResult = val
            //     }
            // },
            //计数
            mulNum(val) {
                let that = this
                that.mulNumber = val
            }
        },
        mounted() {
            if (!this.isAdd) {
                this.mulNumber = this.eMultiResult.length
                this.multiResult = this.eMultiResult
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .multi_container {
    width: 100%;
    min-height: 50px;
    display: flex;
    flex-direction: column;
  }

  .multi_input_con {
    min-width: 500px;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }

  .multi_input_li {
    display: flex;
    align-items: center;
    margin-right: 10px;
  }

  .multi_input_li_title {
    display: inline-block;
    min-width: 100px;
    text-align: center;
  }

  .multi_input_li_title input {
    /*border: none;*/
    /*border-radius: 2px;*/

  }

  .multi_input_li_unit {
    display: inline-block;
    min-width: 40px;
    text-align: left;
    margin-left: 5px;
  }

  .multi_img {
    width: 20px;
    height: 20px;
  }
</style>
