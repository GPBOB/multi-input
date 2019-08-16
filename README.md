# description

Create multiple input at the same time,The number of input can be controlled by buttons 

## install

npm install vue-multi-input --save

## How to use

parameter:  
mulNum --- Control input number  
multiColumns --- Component columns,include:  
title：*title*  
type：*the type of input*  --only input-text
key: parameter name
unit:*unit*  
eMultiColumns --- Component columns like multiInputCol
eMultiResult ---  existing data 
isAdd(Boolean) --- Distinguish between new modules  
To get the results--- methods getMultiData

return [{key1:"",key2:"",}] 



example:  
addData
```
  <vueMultiInput :multiColumns="multiCol" @getMultiData="getResult"></vueMultiInput>

data () {
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
    }
    }
    
```

# 描述
该组件是用于同时创建多个input，类似于检索框一类的样式。可以通过配置控制input
数量，并且有按钮新增删除按钮对input数量进行控制

## 安装
 
 npm install vue-multi-input --save
 
## 使用
参数设置：  
mulNum --- 控制input数量  
multiColumns --- 组件columns(类似于iview的table columns),具体参数:  
title：*标题*  
type：*input类型*  --目前只有input-text
key： *参数名称* 
unit:*单位*  
eMultiColumns --- 编辑的组件columns 和multiInputCol一样
eMultiResult ---编辑组件时，已经有的数据
isAdd(Boolean) --- 区分是新增还是编辑  
获取输入框结果：
    通过getMultiData方法获取
返回数据为 [{key1:"",key2:"",}] 
示例:  
```
<vueMultiInput :multiColumns="multiCol" @getMultiData="getResult"></vueMultiInput>

data () {
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
      ]
    }
    }
```
具体使用方法进入https://github.com/GPBOB/multi-input
 
For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
