<template>
  <div>
    <div id="echart1" ref="echart1"></div>
    <div>{{show}}</div>
  </div>
</template>
<script>
export default {
  name: "echart1",
  data() {
    return {
      aadata: [],
      bbdata: [],
      ccdata: [],
      zydata: [],
      show: []
    };
  },
  mounted() {
    var that = this;
   /*  var e = [1, 2, 3, 4];
    console.log(e.splice(e.indexOf(2), 1));
    console.log(e); */
    var aa = Math.random();
    var cc = [];
    for (var i = 0; i < 100; i++) {
      that.aadata.push(aa);
      that.bbdata.push(i);
      cc.push(0);
    }
    cc.splice(cc.length - 1, 1, that.aadata[that.aadata.length - 1]);
    that.ccdata = cc;
    that.api();
    setInterval(function() {
      that.api();
    }, 1000);
  },
 /*  watch: {
    xdata(re) {
      this.drawLine();
    }
  }, */
  methods: {
    api() {
          var that = this;
          var b =Math.random().toFixed(2);
          that.show=b
          that.aadata.shift();
          /*   .shift() */
          that.bbdata.shift();
          that.aadata.push(b);
          that.bbdata.push(b);
          console.log(that.aadata);
          console.log(that.aadata);
          that.ccdata.splice(that.zydata.length - 1, 1, b);
          console.log(that.zydata);
          /* that.$set(that.xdata.shift()); */
          that.drawLine();
       
    },
    drawLine() {
      var that = this;
      var myChart = this.$echarts.init(this.$refs.echart1);
      myChart.setOption({
        xAxis: {
          type: "category",
          boundaryGap: false,
          data: that.bbdata
        },
        yAxis: {
          type: "value"
          /* max: 0.5 */
        },
        series: [
          {
            data: that.aadata,
            type: "line",
             animation: false,
            smooth: true,
            symbol: "none",
            lineStyle: {
              color: {
                type: "linear",
                /*   x: 0,
    y: 0,
    x2: 0,
    y2: 1, */
                colorStops: [
                  {
                    offset: 0,
                    color: "#0eb92e" // 0% 处的颜色
                  },
                  {
                    offset: 0.8,
                    color: "#0eb92e" // 0% 处的颜色
                  },
                  {
                    offset: 1,
                    color: "#f0e242" // 100% 处的颜色
                  }
                ],
                opacity: 0.4,
                globalCoord: false // 缺省为 false
              }
            }
          },
          {
            name: "最高气温",
            barWidth: 2,
            type: "bar",
            data: that.ccdata,
            animation: false,
            markPoint: {
              animation: false,
              symbol: "emptyCircle",
              data: [{ type: "max" }],
              symbolSize: 16,
              itemStyle: {
                normal: {
                  label: {
                    show: false
                  }
                }
              }
            }
          }
        ]
      });
    }
  }
};
</script>
<style scoped>
#echart1 {
  width: 100%;
  height: 400px;
}
</style>
