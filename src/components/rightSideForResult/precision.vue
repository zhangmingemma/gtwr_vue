<template>
  <div class="precision-canel">
    <div class="chart-container">
      <div class="row">
        <div class="chart" id="scatter"></div>
        <div class="chart" id="force"></div>
        <div class="chart" id="three-d"></div>
      </div>
      <div class="row">
        <div class="chart" id="radar"></div>
        <div class="chart" id="pie"></div>
        <div class="chart" id="line"></div>
      </div>
    </div>
    <div class="text-container">
      <header class="title"><p>精度描述</p></header><!-- /header -->
      <p>查准率计算结果为.......表明<b>美国XXX区人口分布较为集中</b>，原因是该地区经济发展较快......</p>
      <p>XXX计算结果为..........表明。。。。。</p>

    </div>
  </div>
</template>

<script>
import echarts from 'echarts'
import'echarts-gl'
require('../../style/rightSideForResult.scss')

export default {
  name: 'precision',
  data () {
    return {
       
    }
  },
  
  components:{
  },
  mounted(){
    this.drawScatter();
    this.drawThreeD();
    this.drawForce();
    this.drawLine();
    this.drawRadar();
    this.drawPie();
  },
  computed:{
    
  },
  methods:{
    //绘制第一幅散点图
    drawScatter:function(){
      let scatterChart = document.getElementById('scatter');
      let myChart = echarts.init(scatterChart);
      let app = {};
      let option = {
        title : {
            text: '二维散点图',
        },
        grid: {
            left: '3%',
            right: '7%',
            bottom: '3%',
            containLabel: true
        },
        xAxis : [
            {
                type : 'value',
                scale:true,
                axisLabel : {
                    formatter: '{value} '
                },
                splitLine: {
                    show: false
                }
            }
        ],
        yAxis : [
            {
                type : 'value',
                scale:true,
                axisLabel : {
                    formatter: '{value} '
                },
                splitLine: {
                    show: false
                }
            }
        ],
        series : [
            {
                name:'女性',
                type:'scatter',
                data: [[161.2, 51.6], [167.5, 59.0], [159.5, 49.2], [157.0, 63.0], [155.8, 53.6],
                    [170.0, 59.0], [159.1, 47.6], [166.0, 69.8], [176.2, 66.8], [160.2, 75.2],
                    [172.5, 55.2], [170.9, 54.2], [172.9, 62.5], [153.4, 42.0], [160.0, 50.0],
                    [147.2, 49.8], [168.2, 49.2], [175.0, 73.2], [157.0, 47.8], [167.6, 68.8],
                    [159.5, 50.6], [175.0, 82.5], [166.8, 57.2], [176.5, 87.8], [170.2, 72.8],
                    [174.0, 54.5], [173.0, 59.8], [179.9, 67.3], [170.5, 67.8], [160.0, 47.0],
                    [154.4, 46.2], [162.0, 55.0], [176.5, 83.0], [160.0, 54.4], [152.0, 45.8],
                    [162.1, 53.6], [170.0, 73.2], [160.2, 52.1], [161.3, 67.9], [166.4, 56.6],
                    [168.9, 62.3], [163.8, 58.5], [167.6, 54.5], [160.0, 50.2], [161.3, 60.3],
                    [167.6, 58.3], [165.1, 56.2], [160.0, 50.2], [170.0, 72.9], [157.5, 59.8],
                    [167.6, 61.0], [160.7, 69.1], [163.2, 55.9], [152.4, 46.5], [157.5, 54.3],
                    [168.3, 54.8], [180.3, 60.7], [165.5, 60.0], [165.0, 62.0], [164.5, 60.3],
                    [156.0, 52.7], [160.0, 74.3], [163.0, 62.0], [165.7, 73.1], [161.0, 80.0],
                    [162.0, 54.7], [166.0, 53.2], [174.0, 75.7], [172.7, 61.1], [167.6, 55.7],
                    [151.1, 48.7], [164.5, 52.3], [163.5, 50.0], [152.0, 59.3], [169.0, 62.5],
                    [176.5, 71.8], [164.4, 55.5], [160.7, 48.6], [174.0, 66.4], [163.8, 67.3]
                ]
            },
            {
                name:'男性',
                type:'scatter',
                data: [[174.0, 65.6], [175.3, 71.8], [193.5, 80.7], [186.5, 72.6], [187.2, 78.8],
                    [181.5, 74.8], [184.0, 86.4], [184.5, 78.4], [175.0, 62.0], [184.0, 81.6],
                    [180.0, 76.6], [177.8, 83.6], [192.0, 90.0], [176.0, 74.6], [174.0, 71.0],
                    [184.0, 79.6], [192.7, 93.8], [171.5, 70.0], [173.0, 72.4], [176.0, 85.9],
                    [176.0, 78.8], [180.5, 77.8], [172.7, 66.2], [176.0, 86.4], [173.5, 81.8],
                    [178.0, 89.6], [180.3, 82.8], [180.3, 76.4], [164.5, 63.2], [173.0, 60.9],
                    [183.5, 74.8], [175.5, 70.0], [188.0, 72.4], [189.2, 84.1], [172.8, 69.1],
                    [170.0, 59.5], [182.0, 67.2], [170.0, 61.3], [177.8, 68.6], [184.2, 80.1],
                    [186.7, 87.8], [171.4, 84.7], [172.7, 73.4], [175.3, 72.1], [180.3, 82.6],
                    [182.9, 88.7], [188.0, 84.1], [177.2, 94.1], [172.1, 74.9], [167.0, 59.1],
                    [169.5, 75.6], [174.0, 86.2], [172.7, 75.3], [182.2, 87.1], [164.1, 55.2],
                    [163.0, 57.0], [171.5, 61.4], [184.2, 76.8], [174.0, 86.8], [174.0, 72.2],
                    [170.2, 62.3], [177.8, 82.7], [179.1, 79.1], [190.5, 98.2], [177.8, 84.1],
                    [180.3, 83.2], [180.3, 83.2]
                ]          
            }
        ]
      };
      myChart.setOption(option, true);
    },
    //绘制第二幅3d线图
    drawForce:function(){
      let scatterChart = document.getElementById('force');
      let myChart = echarts.init(scatterChart);
      let app = {};
      let data = [{
          fixed: true,
          x: myChart.getWidth() / 5,
          y: myChart.getHeight() / 4,
          symbolSize: 10,
          id: '-1'
      }];

      let edges = [];
      for (let i = 0; i < 50; i++) {
        data.push({
            id: data.length
        });
        let source = Math.round((data.length - 1) * Math.random());
        let target = Math.round((data.length - 1) * Math.random());
        if (source !== target) {
            edges.push({
                source: source,
                target: target
            });
        }
      };
      let option = {
        title:{
          text:'力导向图'
        },
          series: [{
              type: 'graph',
              layout: 'force',
              animation: false,
              data: data,
              force: {
                  // initLayout: 'circular'
                  repulsion: 20,
                  edgeLength: 3
              },
              edges: edges,
              focusNodeAdjacency:true
          }]
      };             
      myChart.setOption(option, true);
    },
    //绘制第三幅3d面图
    drawThreeD:function(){
      let scatterChart = document.getElementById('three-d');
      let myChart = echarts.init(scatterChart);
      let app = {};
      let gaussian = this.makeGaussian(50, 0, 0, 20, 20);

      let data = [];
      for (let i = 0; i < 1000; i++) {
          // x, y 随机分布
          let x = Math.random() * 100 - 50;
          let y = Math.random() * 100 - 50;
          let z = gaussian(x, y);
          data.push([x, y, z]);
      }
      let option = {
          title:{
            text:'三维散点图'
          },
          grid3D: {
            left:20,
            boxWidth:90,
            boxHeight:80,
          },
          xAxis3D: {
            splitNumber:3
          },
          yAxis3D: {
            splitNumber:3
          },
          zAxis3D: { 
            splitNumber:3
          },
          visualMap: {
              calculable: true,
              max: 50,
              // 维度的名字默认就是表头的属性名
              dimension: 2,
              inRange: {
                  color: ['#313695', '#4575b4', '#74add1', '#abd9e9', '#e0f3f8', '#ffffbf', '#fee090', '#fdae61', '#f46d43', '#d73027', '#a50026']
              },
              show:false
          },
          series: [{
              type: 'scatter3D',
              symbolSize:5,
              data: data
          }]
      }
      myChart.setOption(option, true);
    },
    //创建高斯分布点
    makeGaussian:function(amplitude, x0, y0, sigmaX, sigmaY) {
        return function (amplitude, x0, y0, sigmaX, sigmaY, x, y) {
            var exponent = -(
                    ( Math.pow(x - x0, 2) / (2 * Math.pow(sigmaX, 2)))
                    + ( Math.pow(y - y0, 2) / (2 * Math.pow(sigmaY, 2)))
                );
            return amplitude * Math.pow(Math.E, exponent);
        }.bind(null, amplitude, x0, y0, sigmaX, sigmaY);
    },
    drawRadar:function(){
      let scatterChart = document.getElementById('radar');
      let myChart = echarts.init(scatterChart);
      let app = {};
      let option = {
          title: {
              text: '雷达图',
          },
          visualMap: {
              top: 'middle',
              right: 10,
              color: ['red', 'yellow'],
              calculable: true,
              show:false
          },
          radar: {
             indicator : [
                 {  max: 400},
                 {  max: 400},
                 {  max: 400},
                 {  max: 400},
                 {  max: 400}
              ]
          },
          series : (function (){
              var series = [];
              for (var i = 1; i <= 28; i++) {
                  series.push({
                      name:'浏览器（数据纯属虚构）',
                      type: 'radar',
                      symbol: 'none',
                      lineStyle: {
                          width: 1
                      },
                      emphasis: {
                          areaStyle: {
                              color: 'rgba(0,250,0,0.3)'
                          }
                      },
                      data:[
                        {
                          value:[
                              (40 - i) * 10,
                              (38 - i) * 4 + 60,
                              i * 5 + 10,
                              i * 9,
                              i * i /2
                          ],
                          name: i + 2000 + ''
                        }
                      ]
                  });
              }
              return series;
          })()
      };
      myChart.setOption(option, true);
    },
    drawPie:function(){
      let scatterChart = document.getElementById('pie');
      let myChart = echarts.init(scatterChart);
      let app = {};
      let option = {
          title : {
              text: '饼图'
          },
          toolbox: {
              show : false
          },
          calculable : true,
          series : [
              {
                  name:'半径模式',
                  type:'pie',
                  radius : [20, 110],
                  roseType : 'radius',
                  label: {
                      normal: {
                          show: false
                      },
                      emphasis: {
                          show: true
                      }
                  },
                  lableLine: {
                      normal: {
                          show: false
                      },
                      emphasis: {
                          show: true
                      }
                  },
                  data:[
                      {value:10, name:'rose1'},
                      {value:5, name:'rose2'},
                      {value:15, name:'rose3'},
                      {value:25, name:'rose4'},
                      {value:20, name:'rose5'},
                      {value:35, name:'rose6'},
                      {value:30, name:'rose7'},
                      {value:40, name:'rose8'}
                  ]
              }
          ]
      };
      myChart.setOption(option, true);
    },
    drawLine:function(){
      let scatterChart = document.getElementById('line');
      let myChart = echarts.init(scatterChart);
      let app = {};

      let data = [["2000-06-05",116],["2000-06-06",129],["2000-06-07",135],["2000-06-08",86],["2000-06-09",73],["2000-06-10",85],["2000-06-11",73],["2000-06-12",68],["2000-06-13",92],["2000-06-14",130],["2000-06-15",245],["2000-06-16",139],["2000-06-17",115],["2000-06-18",111],["2000-06-19",309],["2000-06-20",206],["2000-06-21",137],["2000-06-22",128],["2000-06-23",85],["2000-06-24",94],["2000-06-25",71],["2000-06-26",106],["2000-06-27",84],["2000-06-28",93],["2000-06-29",85],["2000-06-30",73],["2000-07-01",83],["2000-07-02",125],["2000-07-03",107],["2000-07-04",82],["2000-07-05",44],["2000-07-06",72],["2000-07-07",106],["2000-07-08",107],["2000-07-09",66],["2000-07-10",91],["2000-07-11",92],["2000-07-12",113],["2000-07-13",107],["2000-07-14",131],["2000-07-15",111],["2000-07-16",64],["2000-07-17",69],["2000-07-18",88],["2000-07-19",77],["2000-07-20",83],["2000-07-21",111],["2000-07-22",57],["2000-07-23",55],["2000-07-24",60]];

      let  dateList = data.map(function (item) {
          return item[0];
      });
      let  valueList = data.map(function (item) {
          return item[1];
      });

      let option = {
          visualMap:{
              show: false,
              type: 'continuous',
              seriesIndex: 0,
              min: 0,
              max: 400
          }, 
          title: {
              text: '折线图'
          },
          tooltip: {
              trigger: 'axis'
          },
          xAxis: {
              data: dateList
          },
          yAxis: {
              splitLine: 3
          }, 
          grid: {
              left: '15%'
          }, 
          series: {
              type: 'line',
              showSymbol: false,
              data: valueList
          }
      };
      myChart.setOption(option, true);
    }    
  }
}
</script>
