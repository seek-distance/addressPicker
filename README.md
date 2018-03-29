
# 基于vue省区市三级联动组件

## 如何使用
1. 首先项目需要引入mint-ui(npm install mint-ui)
2. 引入addressPicker文件夹到你的项目中
3. 在你需要引用addressPicker组件的地方引用他，比如

``` bash
<template>
  <address-picker v-model="value"></address-picker>
</template>
<script>
import addressPicker from './addressPicker/addressPicker.vue'
export default {
  components: {
    "address-picker": addressPicker
  },
  data () {
    return {
      value: []
    }
  }
}
</script>
```
## Prop
v-model: 接受一个数组[省份，城市，地区]



# A addressPicker component for Vue
## How to use
1. You need to install mint-ui in your project(npm install mint-ui)
2. import addressPicker folder to your project
3. import addressPicker where you need like

``` bash
<template>
  <address-picker v-model="value"></address-picker>
</template>
<script>
import addressPicker from './addressPicker/addressPicker.vue'
export default {
  components: {
    "address-picker": addressPicker
  },
  data () {
    return {
      value: []
    }
  }
}
</script>
```
## Prop
v-model: accept a Array like [Province, city, area]


