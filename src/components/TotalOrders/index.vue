<template>
  <common-card
    title="累计订单量"
    value="2,123,2233">
    <template>
      <div id="total-order-chart" :style="{width:'100%',height:'100%'}"/>
    </template>

    <template v-slot:footer>
      <span>昨日订单量 </span>
      <span class="emphasis">20,000,000</span>
    </template>
  </common-card>
</template>

<script>
  import commonCardMixin from '../../mixins/commonCardMixin'

  export default {
    mixins: [commonCardMixin],
    mounted () {
      const chartDom = document.getElementById('total-order-chart')
      const chart = this.$echarts.init(chartDom)
      chart.setOption({
        xAxis: {
          type: 'category', // 设置折线图
          show: false,
          boundaryGap: false // 默认图表x轴两侧会有间距，设置不添加间距
        },
        yAxis: {
          show: false // 设置坐标轴不显示
        },
        series: [{
          type: 'line',
          data: [620, 432, 220, 534, 790, 430, 220, 320, 532, 320, 834, 690, 530, 220, 620],
          areaStyle: {
            color: 'purple' // 设置填充色为紫色
          },
          lineStyle: {
            width: 0 // 设置线不可见
          },
          itemStyle: {
            opacity: 0 // 数据点（item）为全透明
          },
          smooth: true // 设置数据点更平滑展示
        }],
        grid: { // 将控件四方缩进去除
          top: 0,
          bottom: 0,
          left: 0,
          right: 0
        }

      })
    }
  }
</script>

<style scoped>

</style>
