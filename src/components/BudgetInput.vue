<template>
  <div class="wrapper">
    <div class="input-content">
      <p class="input-title">
        Введите сумму, чтобы увидеть прогноз по подписчикам и просмотрам
      </p>
      <div class="input-field">
        <input v-model="budget" type="number" @input="onInput" />
        <span class="input-postfix">руб.</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BudgetInput',
  data() {
    return {
      budget: null
    }
  },
  methods: {
    onInput() {
      this.$emit('changeBudget', +this.budget)
    }
  }
}
</script>

<style scoped lang="scss">
.wrapper {
  height: 209px;
  max-width: 590px;
  width: 100%;
  background-color: #e2e5ee;
  border-radius: 6px;
}
.input-content {
  max-width: 412px;
  padding-top: 30px;
  margin: 0 50px;
}
.input-title {
  font-family: 'PT Sans', sans-serif;
  font-size: 20px;
  line-height: 24px;
  margin-bottom: 40px;
  margin-right: 50px;
}
input {
  color: #212121;
  outline: none;
  font-weight: 500;
  border: 1px solid #e2e5ee;
  border-radius: 6px;
  padding: 8px 20px;
  margin-left: 50px;
  margin-right: 20px;
  width: calc(100% - 104px);
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
input[type='number'] {
  -moz-appearance: textfield;
}

.input-field {
  display: flex;
  align-items: center;
  position: relative;
  &::before {
    content: '';
    position: absolute;
    background-color: transparent;
    background-image: url('../assets/ruble.svg');
    width: 30px;
    height: 30px;
    top: 7px;
  }
}
.input-postfix {
  color: #212121;
  font-weight: 500;
}
@media (max-width: 1100px) {
  .input-title {
    font-size: 18px;
    line-height: 23px;
    margin-right: 0;
  }
}
@media (max-width: 960px) {
  .wrapper {
    height: 206px;
    max-width: 502px;
  }
  input {
    font-size: 18px;
    line-height: 31px;
    padding: 7px 20px;
  }
  .input-content {
    max-width: 374px;
    margin-left: 40px;
  }
}
@media (max-width: 768px) {
  .input-content {
    padding-top: 24px;
    margin: 0 20px;
  }
}
@media (max-width: 540px) {
  input {
    font-size: 15px;
    line-height: 26px;
    margin-right: 6px;
    margin-left: 36px;
    width: calc(100% - 74px);
  }
  .input-title {
    font-size: 16px;
    line-height: 20px;
    margin-bottom: 30px;
  }
  .input-postfix {
    font-size: 15px;
    line-height: 25px;
  }
}
@media (max-width: 415px) {
  .wrapper {
    height: 164px;
    border-radius: 0;
  }
  input {
    margin-right: 16px;
    margin-left: 42px;
    width: calc(100% - 90px);
  }
  .input-title {
    max-width: 282px;
  }
}
</style>
