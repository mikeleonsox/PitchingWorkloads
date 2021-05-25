<template>
  <div>
    <b-table small :fields="itemFields" :items="tableItems">
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
        <span>
          <vue-plotly
            :data="data.item.bar"
            :layout="data.item.tableGraphLayout"
            :display-mode-bar="false"
          ></vue-plotly>
          <vue-plotly
            :data="data.item.bar2"
            :layout="data.item.tableGraphLayout"
            :display-mode-bar="false"
          ></vue-plotly
        ></span>
      </template>
    </b-table>
  </div>
</template>


<script>
import VuePlotly from "@statnett/vue-plotly";

export default {
  name: "Plaintable",
  components: {
    VuePlotly,
  },
  props: {},
  data() {
    return {
      // A column that needs custom formatting
      itemFields: [
        { key: "name", label: "Full Name" },
        { key: "chronic", label: "Name" },
        { key: "acRatiosLast20", label: "ac last 5" },
        { key: "bar", label: "chart" },
      ],

      tableItems: [
        {
          name: "Giolito, Lucas",
          chronic: 20.1,
          percentage: 1,
          acRatio: 1.14,
          acRatiosLast20: [20, 0, 0, 0, 0],
          lastWorkloads: [10, 15, 5, 25],
          nextWorkloads: [20, 5, 15, 20],
          bar: [
            {
              x: [1, 2, 3, 4],
              y: [10, 15, 13, 17],
              type: "bar",
              width: [0.2, 0.2, 0.2, 0.2],
            },
          ],

          tableGraphLayout: {
            width: 400,
            height: 300,
          },
          bar2: [
            {
              x: [1, 2, 3, 4],
              y: [33, 35, 3, 17],
              type: "bar",
              width: [0.2, 0.2, 0.2, 0.2],
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
          bar: [
            {
              x: [1, 2, 3, 4],
              y: [60, 15, 13, 17],
              type: "bar",
              width: [0.2, 0.2, 0.2, 0.2],
            },
          ],

          tableGraphLayout: {
            width: 400,
            height: 300,
          },
          bar2: [
            {
              x: [1, 2, 3, 4],
              y: [3, 15, 13, 17],
              type: "bar",
              width: [0.2, 0.2, 0.2, 0.2],
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
