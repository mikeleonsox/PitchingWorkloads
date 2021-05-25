<template>
<div>
  <img style="margin-bottom:100px;" src="../assets/sox_workload.png"/>
  <table  style="text-align: center">
    <tr>
      <th>Name</th>
      <th>Chronic WL</th>
      <th></th>
      <th>AC Ratio</th>
      <th>AC RATIOS LAST 20 (Low/Med/High)<br/><span style="font-size:11px"> <1.2, <1.3, <1.4, <1.5, <1.6</span></th>
      <th class="align-middle">DAILY WORKLOADS</br>(LAST 5, NEXT 5)</th>
    </tr>
    <tr v-for="(item, index) in items">
      <td class="align-middle nameText">{{ item.name }}</td>

      <td class="align-middle pilltext ">
        
           <b-badge pill variant="primary">{{ item.chronic }}</b-badge>
      
        
      </td>
      <td class="align-middle">{{ item.percentage }}%</td>
      <td class="align-middle pilltext">
        <b-badge pill variant="primary">{{ item.acRatio }}</b-badge>
      </td>
      <td class="align-middle slashes">
        {{ item.acRatiosLast20[0] }}/{{ item.acRatiosLast20[1] }}/{{
          item.acRatiosLast20[2]
        }}/{{ item.acRatiosLast20[3] }}
      </td>
      <td>
        <div
          style="float: left; margin: 0px; border: 0px"
          v-bind:id="item.chartPriorId"
        ></div>

        <div
          style="float:left; padding-top:10px; margin: 0px; border: 0px"
          v-bind:id="item.chartAfterId"
        ></div>
      </td>
    </tr>
  </table>
  </div>
</template>

<script src="https://cdn.jsdelivr.net/npm/vega@5.20.2"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega-lite@5.1.0"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega-embed@6.17.0"></script>
<script>
export default {
  name: "Current",
  components: {},
  mounted() {
    this.init();
  },

  methods: {
    init: function () {
      this.items.forEach((item) => {
        vegaEmbed("#" + item.chartPriorId, item.chartBefore, {
          actions: false,
        });
        vegaEmbed("#" + item.chartAfterId, item.chartAfter, { actions: false });
      });
    },
  },
  data() {
    return {
      items: [
        {
          chartPriorId: "chartPriorId",
          chartAfterId: "chartAfterId",
          name: "Giolito, Lucas",
          chronic: 20.1,
          percentage: 1,
          acRatio: 1.14,
          acRatiosLast20: [20, 0, 0, 0, 0],
          lastWorkloads: [10, 15, 5, 45],
          nextWorkloads: [20, 5, 15, 20],

          chartBefore: {
            $schema: "https://vega.github.io/schema/vega-lite/v5.json",
            config: {
              view: { fill: "#d1a8d1" },
            },
            width: 210,
            height: 90,

            data: {
              values: [
                { a: "A", b: 32, color: "#cfcfd0" },
                { a: "B", b: 4, color: "#3db5eb" },
                { a: "C", b: 43, color: "#30a749" },
                { a: "D", b: 43, color: "#7c8085" },
                { a: "E", b: 14, color: "#7c8085" },
              ],
            },
            mark: "bar",
            encoding: {
              color: {
                field: "color",
                type: "nominal",
                scale: null,
              },
              x: { field: "a", type: "nominal", axis: null },
              y: {
                field: "b",
                type: "quantitative",
                axis: { grid: true, tickCount: 1, values: [25, 50] },
                scale: { domain: [0, 50] },
              },
            },
          },

          chartAfter: {
            $schema: "https://vega.github.io/schema/vega-lite/v5.json",
            config: {
              view: { fill: "white" },
              padding: { left: -7, right: 5 },
            },
            width: 210,
            height: 90,
            data: {
              values: [
                { a: "A", b: 5, color: "#cfcfd0" },
                { a: "B", b: 44, color: "#3db5eb" },
                { a: "C", b: 23, color: "#30a749" },
                { a: "D", b: 13, color: "#7c8085" },
                { a: "E", b: 14, color: "#7c8085" },
              ],
            },
            mark: "bar",
            encoding: {
              x: { field: "a", type: "nominal", axis: null },
              y: {
                field: "b",
                type: "quantitative",
                axis: {
                  grid: true,
                  tickCount: 1,
                  values: [25, 50],
                  title: null,
                  labels: false,
                },
                scale: { domain: [0, 50] },
              },
              color: {
                field: "color",
                type: "nominal",
                scale: null,
              },
            },
          },
        },

        {
          chartPriorId: "chartId3",
          chartAfterId: "chartId4",
          name: "Cease, Dylan",
          chronic: 20.1,
          percentage: 1,
          acRatio: 1.14,
          acRatiosLast20: [20, 0, 0, 0, 0],
          lastWorkloads: [10, 15, 5, 25],
          nextWorkloads: [20, 5, 15, 20],

          chartBefore: {
            $schema: "https://vega.github.io/schema/vega-lite/v5.json",
            config: {
              view: { fill: "#d1a8d1" },
            },
            width: 210,
            height: 90,
            data: {
              values: [
                { a: "A", b: 22, color: "#cfcfd0" },
                { a: "B", b: 14, color: "#3db5eb" },
                { a: "C", b: 23, color: "#30a749" },
                { a: "D", b: 43, color: "#7c8085" },
                { a: "E", b: 14, color: "#7c8085" },
              ],
            },
            mark: "bar",
            encoding: {
              x: { field: "a", type: "nominal", axis: null },
              y: {
                field: "b",
                type: "quantitative",
                axis: { grid: true, tickCount: 1, values: [25, 50] },
                scale: { domain: [0, 50] },
              },
              color: {
                field: "color",
                type: "nominal",
                scale: null,
              },
            },
          },
          chartAfter: {
            $schema: "https://vega.github.io/schema/vega-lite/v5.json",
            config: {
              view: { fill: "white" },
              padding: { left: -7, right: 5 },
            },
            width: 210,
            height: 90,
            data: {
              values: [
                { a: "A", b: 18, color: "#cfcfd0" },
                { a: "B", b: 22, color: "#3db5eb" },
                { a: "C", b: 33, color: "#30a749" },
                { a: "D", b: 43, color: "#7c8085" },
                { a: "E", b: 14, color: "#7c8085" },
              ],
            },
            mark: "bar",
            encoding: {
              x: { field: "a", type: "nominal", axis: null },
              y: {
                field: "b",
                type: "quantitative",
                axis: {
                  grid: true,
                  tickCount: 1,
                  values: [25, 50],
                  title: null,
                  labels: false,
                },
                scale: { domain: [0, 50] },
              },
              color: {
                field: "color",
                type: "nominal",
                scale: null,
              },
            },
          },
        },
      ],
    };
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.badge-primary {
  color: black;
  background-color: white;
  border: 2px solid blue;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.nameText {
  font-size: 18px;
}
.pilltext {
  font-size: 22px;
  padding: 10px;
}
.slashes {
  letter-spacing: 3px;
  padding: 10px;
}
.bold {
  font-style: bold;
}
</style>
