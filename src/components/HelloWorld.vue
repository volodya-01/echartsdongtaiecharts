<template>
  <div class="hello">
    <hello/>
 <echart1/>
 <echart2/>
  </div>
</template>

<script>
import hello from '@/components/hello'
import echart1 from '@/components/echart1'
import echart2 from '@/components/echart2'
export default {
  name: 'HelloWorld',
  components:{
    echart1,
    echart2,
    hello
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
