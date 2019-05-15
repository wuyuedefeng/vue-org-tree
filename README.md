Fork from `https://github.com/hukaibaihu/vue-org-tree/blob/master/src/components/org-tree/org-tree.vue`

```
<vue2-org-tree :data="data" collapsable>
  <template slot-scope="{item}">
    {{item.label}} === <button>添加</button><button>详情</button>
  </template>
  <div slot="expandBtn" slot-scope="{isExpanded}">
    <div v-if="isExpanded" style="border: 1px solid #9b9b9b; background: #fff;width: 20px; height: 20px; display: flex; align-items: center; justify-content: center">-</div>
    <div v-else style="border: 1px solid #9b9b9b; background: #fff; width: 20px; height: 20px; display: flex; align-items: center; justify-content: center"> + </div>
  </div>
</vue2-org-tree>
```
