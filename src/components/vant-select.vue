<template>
  <van-popup
      v-model="showPicker"
      :value="true"
      closeable
      position="bottom"
      :style="{ height: '60%' }"
    >
      <!-- <van-search
        :placeholder="placeholder"
        v-model="searchData"
        @search="getColumnList()"
        @input="getColumnList()"
        @clear="getColumnList()"
      ></van-search> -->
      <van-checkbox-group
        ref="checkboxGroup"
        @change="change"
        v-model="checkedValue"
      >
        <van-cell-group>
          <van-cell
            v-for="(item, index) in list"
            clickable
            :key="item.id"
            :title="item.text"
            @click="toggle(index)"
          >
            <template #right-icon>
              <van-checkbox :name="item" ref="checkboxes" shape="square" />
            </template>
          </van-cell>
        </van-cell-group>
      </van-checkbox-group>
    </van-popup>
</template>
<script>
export default {
  props:{
    list:{
      type:Array,
      default:()=>[]
    }
  },
  data(){
    return{
      showPicker:true,
      checkedValue:[]
    }
  },
  methods:{
    change(val){
      console.log(val)
    }
  }
}
</script>