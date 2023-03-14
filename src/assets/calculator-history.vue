<template>
  <div class="history">
    <span>{{ greetingMessage }}</span>
  </div>
</template>

<script>
  export default {
    name: 'CalculatorHistory',
    props: {
        greetingMessage: String
    },
  }
</script>

<style lang="scss" scoped>
    .history {
        background-color: grey;
        color: #fff;
        ul {
            list-style: none;
        }
    }
</style>
