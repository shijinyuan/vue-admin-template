<template>
  <div class="dashboard-container">
    <div class="dashboard-text">name:{{ name }}</div>
    <div class="dashboard-text">roles:<span v-for="role in roles" :key="role">{{ role }}</span></div>
  </div>
</template>

<script>
import {getInfo} from '@/api/hostInfo'

export default {
  name: 'Dashboard',
  data(){
    return {
          name : "hello",
          roles : 'roles'
      }
  }
  ,created() {
      getInfo().then(res => {
          const d = res.data

          if (d.errcode) {
            alert(d.errmsg)
          } else {
            this.name = d.name
            this.roles= d.roles
            console.log(d)
          }
        })
  }

}

</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
