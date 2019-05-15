<template>
  <div class="org-tree-node" :class="{'is-leaf': isLeaf, collapsed: !isLeaf && collapsable && !data[expandKey]}">
    <div class="org-tree-node-label">
      <div class="org-tree-node-label-inner">
        <slot :item="data">
          <span>{{data[labelKey]}}</span>
        </slot>
        <div class="org-tree-node-btn-container" v-if="!isLeaf" :class="{expanded: !isLeaf && data[expandKey]}" @click="$set(data, expandKey, !data[expandKey])">
          <slot name="expandBtn" :isExpanded="!isLeaf && data[expandKey]">
            <div class="org-tree-node-btn"></div>
          </slot>
        </div>
      </div>
    </div>
    <div v-if="!isLeaf && data[expandKey]" class="org-tree-node-children">
      <org-tree-node v-for="(item, idx) in data[childrenKey]" :data="item" :labelKey="labelKey" :childrenKey="childrenKey" :expandKey="expandKey" :horizontal="horizontal" :collapsable="collapsable" :key="idx">
        <template slot-scope="{item: item}">
          <slot :item="item">
            <span>{{item[labelKey]}}</span>
          </slot>
        </template>
        <span slot="expandBtn">
          <slot name="expandBtn" :isExpanded="item[expandKey]"></slot>
        </span>
      </org-tree-node>
    </div>
  </div>
</template>

<script>
export default {
  name: 'org-tree-node',
  props: {
    data: {
      type: Object,
      required: true
    },
    labelKey: { required: true },
    childrenKey: { required: true },
    expandKey: { required: true },
    horizontal: { required: true },
    collapsable: { required: true },
  },
  computed: {
    allSlotKeys () {
      return Object.keys(this.$slots).concat(Object.keys(this.$scopedSlots)).filter((value, index, self) => { return self.indexOf(value) === index })
    },
    isLeaf () {
      return !(Array.isArray(this.data[this.childrenKey]) && this.data[this.childrenKey].length > 0)
    }
  },
  methods: {
  }
}
</script>

