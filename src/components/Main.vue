<template>
  <calculator_item @login="add_expression"/>
  <CalculatorHistory v-for="expression in expressions" v-bind:key="expression.id" :greetingMessage="expression.display_value + '=' + expression.answer_value" />
</template>

<script>
import calculator_item from '@/assets/calculator.vue'
import CalculatorHistory from '@/assets/calculator-history.vue'
  export default {
    name: 'Main-pages',
    components: {
      calculator_item,
      CalculatorHistory,
    },
    data() {
      return {
        expressions: []
      }
    },
    methods: {
      add_expression(data) {
        console.log(data)
        this.expressions.push(data)
        console.log(this.expressions)
      },
    }
}
</script>

<style lang="scss" scoped>

</style>