<template>
  <div class="hello">
    <table class="ui very basic celled table">
      <thead>
        <tr><th class="bump bump_down">Name</th>
        <th class="bump_down">Phenotype</th>
        <th class="bump_down">Company</th>
        <th class="bump_down">THC</th>
        <th class="bump_down">CBD</th>
        <th class="bump_down">Gram</th>
      </tr></thead>
      <tbody v-for="item in info.data.results" :key="item.name">
        <tr>
          <td class="bump" data-label="Name">{{ item.name }}</td>
          <td data-label="Phenotype">{{ item.phenotype }}</td>
          <td data-label="Company">{{ item.company_name }}</td>
          <td data-label="THC">{{ item.thc }}</td>
          <td data-label="CBD">{{ item.cbd }}</td>
          <td data-label="Gram">${{ item.price }}</td>
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
