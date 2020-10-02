<template>
  <div id="app">
    <div class="container">
      <h1 class="title">Прогноз продвижения</h1>
      <div class="grid-row">
        <div class="grid-item text">
          <p>
            Мы пользуемся только официальными инструментами рекламы,
            рекомендуемыми самим YouTube, поэтому все приведенные нами
            просмотры, лайки и комментарии будут настоящими, а подписчики живыми
            и заинтересованными в тематике Вашего канала
          </p>
        </div>
        <div class="grid-item stats">
          <PromoPrediction :budget="budget" />
        </div>
        <div class="grid-item input">
          <BudgetInput @changeBudget="changeBudget" />
        </div>
        <div class="grid-item chart">
          <PredictionChart :budget="budget" />
          <div class="subtext">
            <p>
              Прогноз подписчиков зависит от Вашего контента. Сделайте его
              интересным и старайтесь не снижать планку
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PredictionChart from '@/components/PredictionChart'
import BudgetInput from '@/components/BudgetInput'
import PromoPrediction from '@/components/PromoPrediction'
export default {
  name: 'App',
  components: {
    PredictionChart,
    BudgetInput,
    PromoPrediction
  },
  data() {
    return {
      budget: null
    }
  },
  methods: {
    changeBudget(budget) {
      this.budget = budget
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500&family=PT+Sans:wght@400;700&display=swap');
*,
*::before,
*::after {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  line-height: 26px;
}
.container {
  max-width: 1520px;
  margin: 0 auto;
  padding: 100px 40px 50px;
}
.title {
  font-family: 'PT Sans', sans-serif;
  font-weight: 700;
  color: #212121;
  font-size: 46px;
  line-height: 64px;
  text-align: center;
  margin-bottom: 60px;
}
.grid-row {
  display: flex;
  flex-flow: row wrap;
  position: relative;
}
.grid-item {
  flex-basis: 50%;
  &.text p {
    color: #505361;
    font-weight: 500;
    margin-bottom: 40px;
    max-width: 590px;
  }
  &.chart {
    align-self: flex-end;
    flex: 0 0 auto;
    width: 50%;
    position: relative;
  }
}
.subtext {
  position: absolute;
  color: #717171;
  max-width: 590px;
  width: 100%;
  bottom: 0;
  left: -100%;
  > p {
    font-size: 15px;
    letter-spacing: 0.02em;
    line-height: 22px;
  }
}
@media (max-width: 961px) {
  .container {
    padding: 80px 40px 50px;
  }
  .title {
    font-size: 38px;
    line-height: 50px;
    margin-bottom: 20px;
  }
  .grid-item {
    &.text {
      order: 1;
      flex-basis: 100%;
      text-align: center;
      > p {
        margin-bottom: 30px;
        max-width: 100%;
      }
    }
    &.input {
      order: 2;
      flex-basis: 60%;
    }
    &.stats {
      order: 3;
      flex-basis: 40%;
    }
    &.chart {
      order: 4;
      width: 100%;
      margin-top: 30px;
    }
  }
  .subtext {
    position: static;
    margin-top: 30px;
    max-width: 492px;
  }
}
@media (max-width: 540px) {
  .container {
    padding: 50px 10px;
  }
}
@media (max-width: 415px) {
  .container {
    padding: 50px 0px;
  }
  .title {
    font-size: 32px;
    line-height: 42px;
  }
  .grid-item {
    &.text {
      > p {
        font-size: 15px;
        line-height: 25px;
        margin: 0 20px 30px;
      }
    }
    &.input {
      flex-basis: 100%;
    }
    &.stats {
      flex-basis: 100%;
      margin-top: 16px;
      margin-right: 20px;
      margin-left: 20px;
    }
    &.chart {
      margin-top: 16px;
    }
  }
  .subtext {
    margin-right: 20px;
    margin-left: 20px;
    width: calc(100% - 40px);
    > p {
      font-size: 14px;
      line-height: 20px;
    }
  }
}
</style>
