<template>
  <div class="main">
    <calculator_item @login="add_expression"/>
    <!-- <CalculatorHistory v-for="expression in expressions" v-bind:key="expression.id" :greetingMessage="expression.display_value + '=' + expression.answer_value" /> -->
    <CalculatorHistory :expressions="expressions" @clear_history="clear_history"/>
    <!-- :display_value="display_value" :answer="answer_value" -->
  </div>
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
        expressions: [],
        name: 'hello1'
      }
    },
    methods: {
      add_expression(data) {
        console.log(data)
        this.expressions.push(data)
        console.log(this.expressions)
      },
      clear_history() {
        this.expressions = []
      }
    }
}
</script>

<style lang="scss" scoped>
.main{
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr;
}
</style>