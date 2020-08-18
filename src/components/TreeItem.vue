<template>
  <div class="tree-item">
    <h3>{{node.name}}:{{node.version}}</h3>

    <tree-item v-for="(dep, idx) of lookupDeps(node)"
               :key="idx"
               :node="dep"
               :pkg-list="pkgList"/>

  </div>
</template>

<script>
export default {
  name: 'TreeItem',
  props: {
    node: {
      type: Object,
      required: true
    },
    pkgList: {
      type: Object,
      required: true
    }
  },
  methods: {
    lookupDeps (rootPkg) {
      const depMap = this.pkgList[rootPkg.name].dependencies
      const vm = this
      return Object.keys(depMap).reduce((result, depName) => {
        result.push(vm.pkgList[depName])
        return result
      }, [])
    }
  }
}
</script>

<style scoped>
  .tree-item{
    padding-left: 200px;
  }
</style>
