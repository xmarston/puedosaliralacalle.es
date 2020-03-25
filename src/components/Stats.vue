<style src="animate.css/animate.css">

</style>

<style scoped>

  .facts {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    font-size: 32px;
  }

  .fact {
    padding: 5px;
    flex: 1;
    display: none;
  }

  .not-visible {
    display: none;
  }

  .visible {
    display: block;
  }

  .summary {
    font-size: 42px;
  }

  .summary .definitely-no {
    font-size: 72px;
  }

</style>

<template>

  <div class="stats-component">
    <div class="facts">
      <div class="fact total-cases element1">
        <span>Casos totales</span> <span>{{ countryStats.cases }}</span>
      </div>
      <div class="fact today-cases element2">
        <span>Casos hoy</span> <span>{{ countryStats.todayCases }}</span>
      </div>
      <div class="fact total-deaths element3">
        <span>Muertes totales</span> <span>{{ countryStats.deaths }}</span>
      </div>
      <div class="fact today-deaths element4">
        <span>Muertes hoy</span> <span>{{ countryStats.todayDeaths }}</span>
      </div>
    </div>
    <div class="summary not-visible">
      <p>Viendo estos números sobre el COVID-19 en España, ¿tú que crees?</p>
      <p class="definitely-no">No.</p>
    </div>
  </div>

</template>

<script>

  export default {
    name: 'Stats',
    props: {
      countryStats: Object
    },
    mounted() {
      setTimeout(() => {
        const itemsLenght = 3
        const elementClass = 'element'

        for (let i = 0; i <= itemsLenght; i++) {
          let num = i + 1
          const element = document.querySelector(`.${elementClass}${num}`)
          element.classList.add('animated', 'zoomIn', 'visible')
        }

        setTimeout(this.showSummary, 1000)
      }, 1000)
    },
    methods: {
      showSummary() {
        const summaryElement = document.querySelector('.summary')
        summaryElement.classList.add('zoomIn', 'animated')
        summaryElement.classList.remove('not-visible')
      }
    }
  }

</script>
