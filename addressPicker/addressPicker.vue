<template>
  <mt-picker ref="picker" :slots="pickerSlots" @change="onPickerChange"></mt-picker>
</template>
<script>
  import addressList from './address-data'
  import { Picker } from 'mint-ui';
  import 'mint-ui/lib/picker/style.css'
  export default{
    components: {
      'mt-picker': Picker
    },
    props: ['value'],
    data () {
      return {
        pickerSlots: [
          {
            flex: 1,
            values: [],
          }, {
            flex: 1,
            values: [],
          }, {
            flex: 1,
            values: [],
          }
        ]
      }
    },
    created () {
      this.province = {}
      this.city = {}
      this.pickerSlots[0].values = []
      addressList.forEach(provinceItem => {
        this.pickerSlots[0].values.push(provinceItem.name)  //省份
        this.province[provinceItem.name] = []
        provinceItem.cityList.forEach(cityItem => {
          this.province[provinceItem.name].push(cityItem.name)  //省份-城市
          this.city[cityItem.name] = cityItem.areaList  //城市-区域
        })
      })
      this.address = [this.province, this.city]
      this.value.forEach((item,index) => {
        this.pickerSlots[index].defaultIndex = this.pickerSlots[index].values.indexOf(item)
        if (index !== this.value.length - 1) {
          this.pickerSlots[index + 1].values = this.address[index][item]
        }
      })
      if (!this.value.length) {
        this.pickerSlots[1].values = this.province[this.pickerSlots[0].values[0]]
        this.pickerSlots[2].values = this.city[this.pickerSlots[1].values[0]]
      }
    },
    methods: {
      onPickerChange (picker, values) {
        picker.setSlotValues(1, this.province[values[0]])
        picker.setSlotValues(2, this.city[values[1]])
        this.$emit('input',values)
      }
    }
  }
</script>