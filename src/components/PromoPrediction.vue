<template>
  <div class="wrapper">
    <div class="stats-item">
      <span>+{{ views }}</span
      >просмотров
    </div>
    <div class="stats-item">
      <span>+{{ subs }}</span
      >подписчиков
    </div>
  </div>
</template>

<script>
export default {
  name: 'PromoPrediction',
  props: {
    budget: {
      type: Number,
      default: null
    }
  },
  computed: {
    views() {
      return Math.ceil(this.budget * 4)
    },
    subs() {
      return Math.ceil(this.budget / 8)
    }
  }
}
</script>

<style scoped lang="scss">
.wrapper {
  display: flex;
  justify-content: flex-end;
  margin-left: 30px;
}

.stats-item {
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 240px;
  width: 100%;
  height: 112px;
  background-color: rgba(#bc9af4, 0.3);
  border-radius: 6px;
  text-align: center;
  font-size: 18px;
  line-height: 31px;
  font-weight: 500;
  color: #4b4b4b;
  & + .stats-item {
    margin-left: 24px;
  }
}
span {
  font-family: 'PT Sans', sans-serif;
  color: #212121;
  font-size: 30px;
  line-height: 40px;
  font-weight: bold;
}
@media (max-width: 960px) {
  .wrapper {
    flex-direction: column;
    align-items: flex-end;
  }
  .stats-item {
    width: 100%;
    max-width: 348px;
    max-height: 92px;
    & + .stats-item {
      margin-left: 0;
      margin-top: 22px;
    }
  }
  span {
    font-size: 26px;
    line-height: 28px;
  }
}
@media (max-width: 540px) {
  .wrapper {
    margin-left: 10px;
  }
  .stats-item {
    font-size: 15px;
    line-height: 26px;
  }
  span {
    font-size: 21px;
    line-height: 26px;
  }
}
@media (max-width: 415px) {
  .wrapper {
    flex-direction: row;
    margin-left: 0;
  }
  .stats-item {
    max-width: 179px;
    & + .stats-item {
      margin-top: 0;
      margin-left: 16px;
    }
  }
}
</style>
