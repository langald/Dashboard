<template>
  <div class="chartContainerWrap">
    <div class="chartValueLabel">
      <span class="num">6</span>
      <span>ENTRY</span>
    </div>
    <div class="chartValueLabel chartValueLabel-avg">
      <span class="num">120</span>
      <span>AVG</span>
    </div>
    <div class="chartValueLabel chartValueLabel-exit">
      <span class="num">1200</span>
      <span>EXIT</span>
    </div>
    <div id="chartContainer"></div>
  </div>
</template>
<script>
var Highcharts = require('highcharts');
// require('highcharts/modules/exporting')(Highcharts)

export default {
  name : "ColumnChart",
  props : {
    series : {
      type: Array,
      required: true
    }
  },
  data : function() {
    return {
      target: undefined
    }
  },
  mounted : function() {

    // this function should use if you want to gradient along the all range
    Highcharts.getOptions().plotOptions.column.colors = (function() {
      var colors = [],
      base = '#27e9b6', //Set to the starting color you want.
      i;
      // This is the part you need to setup. 
      //The "50" is just some arbitrarily large value for this demo.
      for (i = 0; i < 22; i += 1) {
        // Start out with a darkened base color (negative brighten), and end
        // up with a much brighter color
        // I modified the math here to use 25 as the increment.
        // Your needs may vary.
        colors.push(Highcharts.Color(base).brighten((i - 3) / 25).get());
      }
      return colors;
    }()),
                
    this.target = Highcharts.chart('chartContainer', {
      chart: {
        type: 'column'
      },
      title: '',   
      yAxis: {
          title: {
              text: ''
          },
          labels: {
            formatter: function () {
              return this.value;
            }
          },
          max: 3000
      },    
      tooltip: {
          headerFormat: '<span style="font-size:10px">{point.key}</span><table>',
          pointFormat: '<tr><td style="padding:0"><b>{point.y:.1f}</b></td></tr>',
          footerFormat: '</table>',
          shared: true,
          useHTML: true
      },
      plotOptions: {
          column: {
              pointPadding: 0.01,
              borderWidth: 0,
              //colorByPoint: true, 
              color: {
                  linearGradient: { x1: 0, y1: 0, x2: 1, y2: 1},
                  stops: [
                      [0, '#27e9b6'],                        
                      [0.6, '#36b2f5'],
                      [1, '#a389d2']
                  ]
              }
          }
      },        
      series: this.series
    })
  },
  beforeDestroy: function() {
    this.target.destroy();
  },
}
</script>

<style scoped>
  .chartContainerWrap {
    position: relative;
    text-align: center;
  }
  #chartContainer {    
    /* min-width: 250px; */
    height: 230px; 
    margin: 40px auto 30px;
  } 
  .chartValueLabel {
    position: absolute;
    top:14px;
    left: 10%;
    width: 64px;
    height: 54px;
    border-radius: 3px;
    color: #fff;
    background-color: #27e9b6;
    text-align: center;
    line-height: 1.2;
    padding: 5px;
    font-size: 12px;
    z-index: 5000;
    /* box-shadow: 0 0 5px 4px #ebebeb; */
    box-shadow: -2px 2px 5px 3px #ebebeb;
  }
  .chartValueLabel .num {
    font-size: 24px;
    display: block;
  }
  .chartValueLabel-avg {
    background-color: #e1e1e1;
    left: 35%;
  }
  .chartValueLabel-exit {
    background-color: #a389d2;
    right: 5%;
    left: auto;
  }
  
  @media screen and (max-width: 500px) {
    .chartValueLabel {
      position: relative;
      top:auto;
      left:auto;
      right:auto;
      display: inline-block;
      margin: 10px 0;
    }
  }
</style>