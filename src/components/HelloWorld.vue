<template>
  <div class="hello">
    <table class="ui very basic celled inverted table">
      <thead>
        <tr><th class="bump bump_down">Strain</th>
        <th class="bump_down">Phenotype</th>
        <th class="bump_down">Company</th>
        <th class="bump_down">THC</th>
        <th class="bump_down">CBD</th>
        <th class="bump_down">Gram</th>
        <th class="bump_down">Eighth</th>
      </tr></thead>
      <tbody v-for="item in info.data.results" :key="item.name">
        <tr>
          <td class="bump" data-label="Name"><h4>{{ item.name }}  <span v-if="item.high_cbd" class="ui mini orange circular label" style="margin-left:1em;">CBD</span>  </h4></td>
          <td v-if="item.phenotype === 'sativa'" data-label="Phenotype" style="background-color: orange;">{{ item.phenotype }}</td>
          <td v-if="item.phenotype === 'hybrid'" data-label="Phenotype" style="background-color: teal;">{{ item.phenotype }}</td>
          <td v-if="item.phenotype === 'indica'" data-label="Phenotype" style="background-color: purple;">{{ item.phenotype }}</td>
          <td data-label="Company">{{ item.company_name }}</td>
          <td data-label="THC">{{ item.thc }}</td>
          <td data-label="CBD">{{ item.cbd }}</td>
          <td data-label="Gram">${{ item.price }}</td>
          <td v-if="item.price === '15.50'" data-label="Eighth">$46.50</td>
          <td v-if="item.price === '13.50'" data-label="Eighth">$40.50</td>
          <td v-if="item.price === '12.00'" data-label="Eighth">$36.00</td>
          <td v-if="item.price === '10.50'" data-label="Eighth">$31.50</td>
          <td v-if="item.price === '9.00'" data-label="Eighth">$27.00</td>
          <td v-if="item.price === '7.50'" data-label="Eighth">$22.50</td>
          <td v-if="item.price === '6.25'" data-label="Eighth">$18.75</td>
        </tr>
      </tbody>
    </table>
    
    <footer>
      <p v-if="info.data.results">Last updated: {{ date }} <span id="foot_counter">Count: {{ info.data.count }}</span></p>
      <p v-else>Connecting to database...</p>
    </footer>

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
      this.date = new Date().toLocaleString() 
    }
  },
  data () {
    return {
      info: null,
      date: null
    }
  },
  mounted () {
    this.getData();
    this.intervalID = setInterval(this.getData.bind(this), 30000);
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
#foot_counter {
  float: right;
  padding-right: 20px;
  color: #ffc609 !important;
}
footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 10px;
  padding-bottom: 20px;
  padding-left: 20px;
  background-color: #494949;
  color: #ff09c2;
  margin-top: 0;
  margin-bottom: 0;
}
</style>
