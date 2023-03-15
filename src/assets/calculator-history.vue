<template>
    <div class="history">
      <h3>   Operations history   </h3>
        <div class="operation-list">
            <li v-for="(expression) in expressions" :key="expression.id">
            <p>{{ expression.display_value }} = {{ expression.answer_value }}</p>
            </li>
        </div>
        <a class="button" @click="clear_history">Clear history</a>
    </div>
</template>

<script>
  export default {
    name: 'CalculatorHistory',
    props: ['expressions'],
    data() {
        return {
            counter: this.expression
        }
    },
    methods: {
        clear_history() {
            this.$emit('clear_history')
        }
    }
  } 
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Itim&display=swap');
.history {
    font-family: 'Itim', cursive;
    background-color: #808080;
    color: black;
    width: 70%;
    display: grid;
    grid-template: 1fr, repeat(2, 1fr); 
    place-items: center;
    ul {
        list-style: none;
    }
    li {
        list-style: none;
    }
    h3 {
        padding: 0 30px 5px 30px;
        border-bottom: 2px solid currentColor;
    }

.operation-list{
    width: 140px;
    height: 250px;
    overflow-y:scroll;
    overflow-x: scroll;
    border-radius: 10px;
    transform: rotate(7deg);
    background-color: #E0C9A6;
    p {
        transform: rotate(-7deg);
    }
}
.button{
  position: relative;
  background-color: #E0C9A6;
  border-radius: 4em;
  font-size: 16px;
  color: black;
  padding: 0.8em 1.8em;
  cursor:pointer;
  user-select:none;
  text-align: center;
  text-decoration: none;
  cursor: pointer;
  transition-duration: 0.4s;
  -webkit-transition-duration: 0.4s; /* Safari */
}

.button:hover {
  transition-duration: 0.1s;
  background-color: #c0ad8f;
}

.button:after {
  content: "";
  display: block;
  position: absolute;
  border-radius: 4em;
  left: 0;
  top:0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: all 0.5s;
  box-shadow: 0 0 10px 40px white;
}

.button:active:after {
  box-shadow: 0 0 0 0 white;
  position: absolute;
  border-radius: 4em;
  left: 0;
  top:0;
  opacity: 1;
  transition: 0s;
}

.button:active {
  top: 1px;
}
    }
</style>
