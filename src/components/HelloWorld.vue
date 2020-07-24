<template>
  <div class="hello">
    <table class="ui very basic celled inverted black table">
      <thead>
        <tr><th class="bump bump_down">Name</th>
        <th class="bump_down">Phenotype</th>
        <th class="bump_down">Company</th>
        <th class="bump_down">THC</th>
        <th class="bump_down">CBD</th>
        <th class="bump_down">Gram</th>
        <th class="bump_down">Eighth</th>
      </tr></thead>
      <tbody v-for="item in info.data.results" :key="item.name">
        <tr>
          <td class="bump" data-label="Name"><h4>{{ item.name }}</h4></td>
          <td v-if="item.phenotype === 'sativa'" data-label="Phenotype" style="background-color: orange;">{{ item.phenotype }}</td>
          <td v-if="item.phenotype === 'hybrid'" data-label="Phenotype" style="background-color: teal;">{{ item.phenotype }}</td>
          <td v-if="item.phenotype === 'indica'" data-label="Phenotype" style="background-color: purple;">{{ item.phenotype }}</td>
          <td data-label="Company">{{ item.company_name }}</td>
          <td data-label="THC">{{ item.thc }}</td>
          <td data-label="CBD">{{ item.cbd }}</td>
          <td data-label="Gram">${{ item.price }}</td>
          <td v-if="item.price === '13.50'" data-label="Eighth">$40.50</td>
          <td v-if="item.price === '12.00'" data-label="Eighth">$36.00</td>
          <td v-if="item.price === '10.50'" data-label="Eighth">$31.50</td>
          <td v-if="item.price === '9.00'" data-label="Eighth">$27.00</td>
          <td v-if="item.price === '7.50'" data-label="Eighth">$22.50</td>
          <td v-if="item.price === '6.25'" data-label="Eighth">$18.25</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    secret: String
  },
  methods: {
    getData: function() {
      axios
      .get('https://www.portlandcannabis.com/api/flower/?limit=50')
      .then(response => (this.info = response))  
    }
  },
  data () {
    return {
      info: null
    }
  },
  mounted () {
    this.getData();
    this.intervalID = setInterval(this.getData.bind(this), 10000);
  }
}
</script>

<style>
.bump {
  padding-left: 1em !important;
}
.bump_down {
  padding-top: 1em !important;
}
</style>
