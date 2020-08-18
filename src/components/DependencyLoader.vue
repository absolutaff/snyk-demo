<template>
    <div class="dependency-loader">

      <div class="dependency-loader__loader">
        LOADER HERE
        <input type="text" v-model="pkgName">
        <input type="text" v-model="pkgVersion">
        <button :disabled="!pkgName || !pkgVersion"
                @click="loadTree">
          LOAD
        </button>
      </div>

      <div class="dependency-loader__tree">
        <tree-item v-if="rootPackage" :node="rootPackage" :pkg-list="pkgsList"/>
      </div>
    </div>
</template>

<script>

import axios from 'axios'
import TreeItem from './TreeItem'

export default {
  name: 'DependencyLoader',
  components: { TreeItem },
  data () {
    return {
      pkgName: undefined,
      pkgVersion: undefined,
      pkgsList: {}
    }
  },
  methods: {
    loadTree () {
      axios.get(`http://localhost:3000/${this.pkgName}/${this.pkgVersion}`).then(res => {
        this.pkgsList = res.data
      })
    }
  },
  computed: {
    rootPackage () {
      if (!this.pkgName) return
      return this.pkgsList[this.pkgName]
    }
  }
}
</script>

<style scoped>

</style>
