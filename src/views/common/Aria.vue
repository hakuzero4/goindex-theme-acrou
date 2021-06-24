<template>
  <div class="aria">
    <el-progress :percentage="100" status="success"></el-progress>
    <el-progress :percentage="100" status="warning"></el-progress>
    <el-progress :text-inside="true" :stroke-width="20" :percentage="50" status="exception"></el-progress>
  </div>
</template>
<script>
export default {
  data() {
    return {
      AraiaId: '',
    }
  },
  mounted() {
    this.getInfo();
  },
  methods: {
    getInfo() {
      const data = {
        "jsonrpc": "2.0",
        "method": "aria2.tellActive",
        "params": ["token:hakuzero", ["gid", "totalLength", "completedLength", "uploadSpeed", "downloadSpeed", "connections", "numSeeders", "seeder", "status", "errorCode", "verifiedLength", "verifyIntegrityPending", "files", "bittorrent", "infoHash"]]
      }

      this.axios.post('http://home.hakuzero.top:6800/jsonrpc', data)
      .then((res) => {
        console.log(res)
      })
    }
  }
}

</script>
<style>
.aria {
  position: fixed;
  width: 300px;
  background: #333;
  bottom: 0;
  top: 0;
}
</style>
