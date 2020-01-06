<template>
  <div class="expand">
     <p class="warn-content">
      <a href="https://xiaoniezi.github.io/2017-10-16/vue-ElementUI-tree-expand/" target="_blank">Tree组件参考
      </a>
    </p>
    <div>
      <TreeRender/>
    </div>
  </div>
</template>
<!-- VUE饿了么树形控件添加增删改功能按钮 -->
<script>
import TreeRender from '@/components/nx-tree'

export default{
  name: 'tree',
  data() {
    return {

    }
  },
  components: {
    TreeRender
  }

}
</script>

<style>
.expand{
  width:100%;
  height:100%;
  overflow:hidden;
}
</style>
