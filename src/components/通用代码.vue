<template>
   <div class="com-container">
     <div class="com-chart" ref="trend_ref"></div>
   </div>
</template>

<script>
export default {
  data () {
    return {
      chartInstance: null,
      allData: null // 从服务器中获取的所有数据
    }
  },
  mounted () {
    this.initChart()
    this.getData()
    // 在页面加载完成的时候, 主动进行屏幕的适配
    window.addEventListener('resize', this.screenAdapter)
    // 在页面加载完成的时候, 主动进行屏幕的适配
    this.screenAdapter()
  },
  destroyed () {
    // 在组件销毁的时候, 需要将监听器取消掉
    window.removeEventListener('resize', this.screenAdapter)
  },
  methods: {
    // 初始化echartInstance对象
    initChart () {
      this.chartInstance = this.$echarts.init(this.$refs.trend_ref, 'chalk')
      const initOption = {}
      this.chartInstance.setOption(initOption)
    },
    // 获取服务器的数据
    async getData () {
      // await this.$http.get()
      // 对allData进行赋值
      // const { data: ret } = await this.$http.get('trend')
      this.updateChart()
    },
    // 更新图表
    updateChart () {
      const dataOption = {}
      this.chartInstance.setOption(dataOption)
    },
    // 当浏览器的大小发生变化的时候, 会调用的方法, 来完成屏幕的适配
    screenAdapter () {
      const adapterOption = {}
      this.chartInstance.setOption(adapterOption)
      this.chartInstance.resize()
    }
  }
}
</script>
<style lang="less" scoped>

</style>
