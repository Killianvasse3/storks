<template>
  <div class="all">
    <div class="center">
      <div class="all2">
        <div id="border">
          <v-chart class="chart" :option="option" />
          <v-chart class="chart" :option="option2" />
          <v-chart class="chart" :option="option3" />
        </div>
        <div id="daron">
          <v-chart class="chart" :option="opti" />
        </div>
      </div>
        <v-chart class="chart2" :option="opetit" />
      <div class="all2">
        <v-chart class="chart3" :option="style" />
        <v-chart class="chart4" :option="quentin" />
      </div>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts/core';
import {
    ParallelChart,
    BarChart,
    PieChart,
    LineChart,
    GraphChart,
    HeatmapChart,
    EffectScatterChart,
    ScatterChart
} from 'echarts/charts';
import { use } from "echarts/core";
import { CanvasRenderer } from "echarts/renderers";
import {
  CalendarComponent,
  GridComponent,
  TitleComponent,
  ToolboxComponent,
  TooltipComponent,
  LegendComponent,
  ParallelComponent,
  VisualMapComponent
} from "echarts/components";
import VChart, { THEME_KEY } from "vue-echarts";
import { ref, defineComponent } from "vue";

use([
  CalendarComponent,
  ParallelComponent,
  ToolboxComponent,
  VisualMapComponent,
  ParallelChart,
  BarChart,
  CanvasRenderer,
  PieChart,
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  GridComponent,
  LineChart,
  GraphChart,
  HeatmapChart,
  EffectScatterChart,
  ScatterChart,
  CanvasRenderer
]);
function getVirtulData(year) {
    year = year || '2017';
    var date = +echarts.number.parseDate(year + '-01-01');
    var end = +echarts.number.parseDate((+year + 1) + '-01-01');
    var dayTime = 3600 * 24 * 1000;
    var data = [];
    for (var time = date; time < end; time += dayTime) {
        data.push([
            echarts.format.formatTime('yyyy-MM-dd', time),
            Math.floor(Math.random() * 300)
        ]);
    }
    console.log(data[data.length - 1]);
    return data;
}
var graphData = [
    [
       '2017-02-01',
        260
    ],
    [
        '2017-02-04',
        200
    ],
    [
        '2017-02-09',
        279
    ],
    [
        '2017-02-13',
        847
    ],
    [
        '2017-02-18',
        241
    ],
    [
        '2017-02-23',
        411
    ],
    [
        '2017-02-27',
        985
    ]
];
var links = graphData.map(function (item, idx) {
    return {
        source: idx,
        target: idx + 1
    };
});
links.pop();
var colorPalette = ['#2998b3', '#Fe8007', '#801e7f', '#Ce5e18']
export default defineComponent({
  name: "HelloWorld",
  components: {
    VChart
  },
  provide: {
    [THEME_KEY]: "dark"
  },
  setup: () => {
    const option = ref({
      title: {
        text: "Capacity of work rooms and blocks",
        left: "center",
        textStyle: {
            fontSize: 14
        }
      },
            
      tooltip: {
        trigger: "item",
        formatter: "{a} <br/>{b} : {c} ({d}%)"
      },
      legend: {
        orient: "vertical",
        left: "left",
        top: 35,
        data: ["Blocks disponible", "Blocks occuped", "Work rooms disponible", "Work rooms occuped"]
      },
      series: [
        {
          name: "Traffic Sources",
          type: "pie",
          radius: "40%",
          center: ["50%", "70%"],
          data: [
            { value: 5, name: "Blocks disponible" },
            { value: 2, name: "Blocks occuped" },
            { value: 5, name: "Work rooms disponible" },
            { value: 2, name: "Work rooms occuped" }
          ],
          color: colorPalette,
          emphasis: {
            itemStyle: {
              shadowBlur: 10,
              shadowOffsetX: 0,
              shadowColor: "rgba(0,0,0,0.5)"
            }
          } 
        }
      ],
    });
    const option2 = ref({
      title: {
        text: "Current bed capacity for infant",
        left: "center",
        textStyle: {
            fontSize: 14
        }
      },
      tooltip: {
        trigger: "item",
        formatter: "{a} <br/>{b} : {c} ({d}%)"
      },
      legend: {
        orient: "vertical",
        left: "left",
        top: 40,
        data: ["Disponible", "Occuped"]
      },
      series: [
        {
          name: "Traffic Sources",
          type: "pie",
          radius: "50%",
          center: ["50%", "60%"],
          data: [
            { value: 280, name: "Disponible" },
            { value: 80, name: "Occuped" }
          ],
          color: colorPalette,
          emphasis: {
            itemStyle: {
              shadowBlur: 10,
              shadowOffsetX: 0,
              shadowColor: "rgba(0,0,0,0.5)"
            }
          } 
        }
      ],
    });
    const option3 = ref({
      title: {
        text: "Current bed capacity for pregnant women",
        left: "center",
        textStyle: {
            fontSize: 12
        }
      },
      tooltip: {
        trigger: "item",
        formatter: "{a} <br/>{b} : {c} ({d}%)"
      },
      legend: {
        orient: "vertical",
        left: "left",
        top: 40,
        data: ["Disponible", "Occuped"]
      },
      series: [
        {
          name: "Traffic Sources",
          type: "pie",
          radius: "50%",
          center: ["50%", "60%"],
          data: [
            { value: 53, name: "Disponible" },
            { value: 254, name: "Occuped" }
          ],
          color: colorPalette,
          emphasis: {
            itemStyle: {
              shadowBlur: 10,
              shadowOffsetX: 0,
              shadowColor: "rgba(0,0,0,0.5)"
            }
          } 
        }
      ],
    });
    const opti = ref({
    title: {
      text: "Forecast figures for next week",
      left: "center"
    },
    xAxis: {
        type: 'category',
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    yAxis: {
        name: 'Born children',
        type: 'value'
    },
    series: [{
        data: [820, 932, 901, 934, 1290, 1330, 1320],
        type: 'line',
        smooth: true,
        color: '#ba0379'
    }]
});
const opetit = ref({
 title: {
      text: "Number of births by day",
      left: "center"
    },
 xAxis: {
        type: 'category',
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    yAxis: {
        name: 'Born children',
        type: 'value'
    },
    series: [{
        data: [120, 200, 150, 80, 70, 110, 130],
        type: 'bar',
        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: 'rgba(255, 191, 0)'
                }, {
                    offset: 1,
                    color: 'rgba(224, 62, 76)'
                }])
    }]
});
  const style = ref({
    title: {
      text: "Provisional calendar of ",
      subtext: "births for the month",
      left: 550,
      top: 90,
      textStyle: {
      fontSize: 19
    },
      subtextStyle: {
      fontSize: 20,
      fontWeight: "bold"
    }
    },
    visualMap: {
        visualMap: [{
        min: 0,
        max: 1000,
        calculable: true,
        orient: 'horizontal',
        bottom: 20
    }, {
        min: 0,
        max: 1000,
        inRange: {
            color: ['grey'],
            opacity: [0, 0.3]
        },
        controller: {
            inRange: {
                opacity: [0.3, 0.6]
            },
            outOfRange: {
                color: '#ccc'
            }
        },
        orient: 'horizontal',
        left: '10%',
        bottom: 20
    }],
    },
    calendar: {
        orient: 'vertical',
        yearLabel: {
            margin: 40
        },
        dayLabel: {
            firstDay: 1,
            nameMap: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        monthLabel: {
            fontSize: 17,
            margin: 30
        },
        cellSize: 50,
        top: 70,
        left: 160,
        range: '2017-02'
    },
    series: [{
        type: 'graph',
        coordinateSystem: 'calendar',
        links: links,
        symbolSize: 10,
        data: graphData
    }, {
        type: 'heatmap',
        coordinateSystem: 'calendar',
        data: getVirtulData(2017)
    },]
  });
  const quentin =ref({
    color: ['#37A2FF', '#FFBF00'],
    title: {
        text: 'Number of births/death in 1 month'
    },
    tooltip: {
        trigger: 'axis',
        axisPointer: {
            type: 'cross',
            label: {
                backgroundColor: '#6a7985'
            }
        }
    },
    legend: {
        data: ['Line 1', 'Line 2']
    },
    grid: {
        left: '3%',
        right: '3%',
        bottom: '3%',
        containLabel: true
    },
    xAxis: [
        {
            type: 'category',
            boundaryGap: false,
            data: ['01', '05', '09', '14', '17', '21', '26']
        }
    ],
    yAxis: [
        {
            name: 'Child',
            type: 'value'
        }
    ],
    series: [
        {
            name: 'Line 1',
            type: 'line',
            stack: '总量',
            smooth: true,
            lineStyle: {
                width: 0
            },
            showSymbol: false,
            areaStyle: {
                opacity: 0.8,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: 'rgba(55, 162, 255)'
                }, {
                    offset: 1,
                    color: 'rgba(116, 21, 219)'
                }])
            },
            emphasis: {
                focus: 'series'
            },
            data: [320, 132, 201, 334, 190, 130, 220]
        },
        {
            name: 'Line 2',
            type: 'line',
            stack: '总量',
            smooth: true,
            lineStyle: {
                width: 0
            },
            showSymbol: false,
            label: {
                show: true,
                position: 'top'
            },
            areaStyle: {
                opacity: 0.8,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: 'rgba(255, 191, 0)'
                }, {
                    offset: 1,
                    color: 'rgba(224, 62, 76)'
                }])
            },
            emphasis: {
                focus: 'series'
            },
            data: [220, 302, 181, 234, 210, 290, 150]
        }
    ]
  });

    return { option, option2, option3, opti, opetit, style, quentin };
  }
});
</script>

<style>
#border{
  border: 1px solid white;
  border-radius: 13px;
  display: flex;
  flex-direction: row;
  width: 100%;
}
#daron{
  border: 1px solid white;
  border-radius: 13px;
  width: 100%;
}
.all {
  margin-top: 0.6%;
  display: flex;
  justify-content: row;
}
.all2 {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.center {
  width: 100%;
  display: flex;
  flex-direction: column;
}
.chart {
  height: 330px;
  border-radius: 13px;
}
.chart2 {
  height: 250px;
  border: solid 1px white;
  border-radius: 13px;
}
.chart3 {
  height: 330px;
  border: solid 1px white;
  border-radius: 13px;
}
.chart4 {
  height: 330px;
  border: solid 1px white;
  border-radius: 13px;
}
</style>