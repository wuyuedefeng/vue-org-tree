<template>
  <div class="hello">
    <vue2-org-tree :data="data" collapsable>
      <template slot-scope="{item}">
        {{item.label}} === <button>添加</button><button>详情</button>
      </template>
      <div slot="expandBtn" slot-scope="{isExpanded}">
        <div v-if="isExpanded" style="border: 1px solid #9b9b9b; background: #fff;width: 20px; height: 20px; display: flex; align-items: center; justify-content: center">-</div>
        <div v-else style="border: 1px solid #9b9b9b; background: #fff; width: 20px; height: 20px; display: flex; align-items: center; justify-content: center"> + </div>
      </div>
    </vue2-org-tree>
  </div>
</template>

<script>
import Vue from 'vue'
import Vue2OrgTree from './org-tree'
Vue.use(Vue2OrgTree)
  export default {
  name: 'HelloWorld',
  data () {
    return {
      data: {
        label: '1', children: [
          {label: '11', children: [
              {label: '111'},
              {label: '112'},
              {label: '113'}
            ]},
          {label: '12'},
          {label: '13', children: [
              {label: '131'},
              {label: '132'},
              {label: '133'}
            ]}
        ],
        expand: true
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
