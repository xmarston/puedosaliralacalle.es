<style scoped>

  h1 {
    display: flex;
    justify-content: center;
  }

  .warning-component {
    width: 100%;
    height: 100%;
  }

</style>

<template>

  <div class="warning-component">
    <img src="@/assets/virus.png" alt="COVID-19 Icon">
    <h1>Mmmmmm deja que lo piense...</h1>
    <Stats :countryStats="countryStats"/>
  </div>

</template>

<script>

  import Stats from './Stats'
  import axios from 'axios'

  export default {
    name: 'Warning',
    components: {
      Stats
    },
    data: () => {
      return {
        COUNTRY: 'Spain',
        COVID19_STATS_URL: 'https://corona.lmao.ninja/countries',
        countryStats: {}
      }
    },
    mounted() {
      this.retrieveStats()
    },
    methods: {
      retrieveStats() {
        axios
          .get(this.COVID19_STATS_URL)
          .then(response => {
            this.showStats(response.data)
          })
          .catch(error => {
            console.log(error)
          })
      },
      showStats(stats) {
        stats.forEach(item => {
          if (item.country == this.COUNTRY) {
            this.countryStats = item
          }
        })
      }
    }
  }

</script>
