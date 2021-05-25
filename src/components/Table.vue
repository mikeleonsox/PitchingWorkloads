<template>
  <div>
    <b-table small :fields="fields" :items="items">
      <!-- A custom formatted column -->
      <template #cell(name)="data">
        <b>{{ data.item.name }} </b>
      </template>
      <template #cell(chronic)="data">
        <b-badge pill variant="primary">{{ data.item.chronic }}</b-badge>
      </template>
      <template #cell(acRatiosLast20)="data">
        <span class="slashes"
          >{{ data.item.acRatiosLast20[0] }}/{{
            data.item.acRatiosLast20[1]
          }}/{{ data.item.acRatiosLast20[2] }}/{{ data.item.acRatiosLast20[3] }}
        </span>
      </template>
      <template #cell()="data">
        <vue-plotly
          :layout="data.item.chartDatalayout"
          :options="data.item.chartDataoptions"
          :data="data.item.chartData"
        />
      </template>
    </b-table>
  </div>
</template>


<script>
import VuePlotly from "@statnett/vue-plotly";

export default {
  name: "Table",
  components: {
    VuePlotly,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      layout: {
        height: 600,
        width: 400,
      },
      options: {},
      fields: [
        // A column that needs custom formatting
        { key: "name", label: "Full Name" },
        { key: "chronic", label: "Name" },
        { key: "acRatiosLast20", label: "ac last 5" },
        { key: "chartData", label: "chart" },
      ],

      pill_color: "warning",
      items: [
        {
          name: "Giolito, Lucas",
          chronic: 20.1,
          percentage: 1,
          acRatio: 1.14,
          acRatiosLast20: [20, 0, 0, 0, 0],
          lastWorkloads: [10, 15, 5, 25],
          nextWorkloads: [20, 5, 15, 20],
          chartData: [
            {
              x: ["1", "2", "3"],
              y: [44, 44, 44],

              type: "bar",
            },
          ],
        },
        {
          name: "Giolito, Lucas",
          chronic: 20.1,
          percentage: 1,
          acRatio: 1.14,
          acRatiosLast20: [20, 0, 0, 0, 0],
          lastWorkloads: [10, 15, 5, 25],
          nextWorkloads: [20, 5, 15, 20],
          chartData: [
            {
              x: ["1", "2", "3"],
              y: [44, 44, 44],

              type: "bar",
            },
          ],
        },
      ],
    };
  },
};
</script>
 
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
.pilltext {
  color: white;
  font-size: 20px;
  padding: 10px;
}
.slashes {
  letter-spacing: 3px;
  padding: 10px;
}
</style>
