<template>
  <div class="nx-data-display">
    <el-row :gutter="10">
      <el-col v-for="(item,index) in data" :key="index" :xs="24" :sm="8" >
        <el-card class="clearfix title_svg">
          <div class="svg_box">
            <div class="svg_item">
              <svg-icon icon-class="today" style="color: red" />
            </div>
          </div>
          <div class="item" :style="{color:color}">
            <h5 class="count"><nx-count-up :start="14" :end="item.count"/></h5>
            <span class="splitLine" />
            <p class="title">{{item.title}}</p>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import nxCountUp from '@/components/nx-count-up/index.vue'
export default {
  name: 'nx-data-display',
  components: {
    nxCountUp
  },
  data() {
    return {
      data: this.option.data,
      color: this.option.color || 'rgb(63, 161, 255)'
    }
  },
  props: {
    option: {
      type: Object,
      default: () => {}
    }
  },
  created() {},
  methods: {}
}
</script>
