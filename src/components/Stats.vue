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

  .summary .big-response {
    font-size: 72px;
  }

</style>

<template>

  <div class="stats-component">
    <div class="facts">
      <div class="fact total-cases element1">
        <span>Casos totales</span><br><span>{{ countryStats.cases }}</span>
      </div>
      <div class="fact today-cases element2">
        <span>Casos hoy</span><br><span>{{ countryStats.todayCases }}</span>
      </div>
      <div class="fact total-deaths element3">
        <span>Muertes totales</span><br><span>{{ countryStats.deaths }}</span>
      </div>
      <div class="fact today-deaths element4">
        <span>Muertes hoy</span><br><span>{{ countryStats.todayDeaths }}</span>
      </div>
    </div>
    <div class="summary not-visible">
      <p>Viendo estos números sobre el COVID-19 en España, ¿tú que crees?</p>
      <p class="big-response">{{ bigResponse }}</p>
    </div>
  </div>

</template>

<script>

  export default {
    name: 'Stats',
    props: {
      countryStats: Object
    },
    data: () => {
      return {
        bigResponse: 'No'
      }
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

        this.analyzeDataToUpdateBigResponse()

        setTimeout(this.showSummary, 1000)
      }, 1000)
    },
    methods: {
      showSummary() {
        const summaryElement = document.querySelector('.summary')
        summaryElement.classList.add('zoomIn', 'animated')
        summaryElement.classList.remove('not-visible')

        this.scrollSmoothly()
      },
      scrollSmoothly() {
        window.scrollTo(0, document.body.scrollHeight)
      },
      analyzeDataToUpdateBigResponse() {
        if (this.countryStats.todayCases === 0 && this.countryStats.todayDeaths === 0 && this.countryStats.cases < 500) {
          this.bigResponse = "¡¡Sí!!"
        }
      }
    }
  }

</script>
