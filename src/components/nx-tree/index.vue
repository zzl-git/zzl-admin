<template>
  <div>
    <el-tree
      class="filter-tree"
      :data="treeList"
      node-key="id"
      show-checkbox
      :check-strictly="true"
      :check-on-click-node="true"
      :expand-on-click-node="false"
      :filter-node-method="filterNode"
      default-expand-all
      @check="handleCheckChange"
      ref="tree"
    >
    </el-tree>
  </div>
</template>

<script>
import api from '@/api/treeApi'
export default{
  name: 'nx-tree',
  data() {
    return {
      treeList: []
    }
  },
  created() {
    this.getTreeList()
  },
  methods: {
    filterNode(value, data) {
      if (!value) return true
      return data.label.indexOf(value) !== -1
    },
    handleCheckChange(data ,checked) {
      checked.checkedKeys.forEach(v => {
        if(v != data.id){
          this.$refs.tree.setChecked(v, false)
        }else{
          this.$emit('update:orgId',v)
          
          this.$refs.tree.setChecked(v, true)
        }
      })
    },
    getTreeList() {
      api.treelist.map(function(v) {
        this.push({
          id: v.id,
          label: v.name,
          children: v.children ? v.children.map(function(v1) {
            return {
              id: v1.id,
              label: v1.name
            }
          }) : []
        })
      }, this.treeList)
    }
  }
}
</script>

<style>

</style>
