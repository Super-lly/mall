<template>
  <div>
    {{iid}}
  </div>
</template>

<script>
export default {
  name : 'detail',
  data(){
    return{
      iid:null
    }
  },
  created(){
    this.iid = this.$route.params.iid
  }
}
</script>