<template>
  <div class="org-tree-container">
    <div class="org-tree" :class="{horizontal, collapsable}">
      <org-tree-node
        :data="data" :labelKey="labelKey" :childrenKey="childrenKey" :expandKey="expandKey"
        :horizontal="horizontal" :collapsable="collapsable"
      >
        <slot slot-scope="{item: item}" :item="item"></slot>
        <span class="org-tree-node-btn" slot="expandBtn" slot-scope="{isExpanded: isExpanded}">
          <slot name="expandBtn" :isExpanded="isExpanded"></slot>
        </span>
      </org-tree-node>
    </div>
  </div>
</template>

<script>
// import render from './node'
import OrgTreeNode from './org-tree-node'
export default {
  name: 'Vue2OrgTree',
  props: {
    data: {
      type: Object,
      required: true
    },
    labelKey: {
      default: 'label'
    },
    childrenKey: {
      default: 'children'
    },
    expandKey: {
      default: 'expand'
    },
    horizontal: {
      type: Boolean,
      default: false
    },
    collapsable: {
      type: Boolean,
      default: false
    },
  },
  components: {
    OrgTreeNode
  }
}
</script>

<style lang="scss">
@import './styles/org-tree';
</style>
