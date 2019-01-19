<template>
  <div>
    <h3>Select</h3>
    <select v-model="country" @change="change_country">
      <option v-for="(c , i) in country_list" :key="i" :value="c.value">{{ c.text }}</option>
    </select>
    <center v-if="country">
      <table>
        <thead>
          <th>key</th>
          <th>value</th>
        </thead>
        <tbody>
          <tr v-for="(k , i) in Object.keys(country)" :key="i">
            <td>{{ k }}</td>
            <td>{{ country[k] }}</td>
          </tr>
        </tbody>
      </table>
    </center>
  </div>
</template>

<script>
export default {
  name: "SelectSample",
  data: function() {
    return {
      country: null
    };
  },
  computed: {
    country_list: () => {
      return [
        { value: null, text: "国を選択してください。" },
        {
          value: {
            name: "中華人民共和国",
            alpha: "CHN",
            population: 1349335152
          },
          text: "中華人民共和国"
        },
        {
          value: { name: "インド", alpha: "IND", population: 1224514327 },
          text: "インド"
        },
        {
          value: {
            name: "アメリカ合衆国",
            alpha: "USA",
            population: 310383948
          },
          text: "アメリカ合衆国"
        }
      ];
    }
  },
  watch: {
    /*
    country: selected_country => {
      console.log(JSON.stringify(selected_country));
    }
    */
  },
  methods: {
    change_country: function() {
      console.log(JSON.stringify(this.country));
    }
  }
};
</script>

<style scoped>
table {
  margin: 0 auto;
  border-collapse: collapse;
}
table th,
table td {
  padding: 0.2rem 2rem;
  border: solid 1px #333;
}
</style>