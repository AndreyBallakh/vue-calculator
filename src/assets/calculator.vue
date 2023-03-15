<template>
    <div class="calculator-body">
        <input class="display" id="input_value" v-model="this.display_value">
        <div class="calculator" @click="update_expression">
            <button class="button ac" @click="clear_display">AC</button>
            <button class="button sign" @click="add_brackets">( )</button>
            <button class="button percent" @click="delete_value">&#8656;</button>
            <button class="button operator" @click="math_operations('/')">&divide;</button>
            <button class="button number" @click="update_number(7)">7</button>
            <button class="button number" @click="update_number(8)">8</button>
            <button class="button number" @click="update_number(9)">9</button>
            <button class="button operator" @click="math_operations('*')">&times;</button>
            <button class="button number" @click="update_number(4)">4</button>
            <button class="button number" @click="update_number(5)">5</button>
            <button class="button number" @click="update_number(6)">6</button>
            <button class="button operator" @click="math_operations('-')">&minus;</button>
            <button class="button number" @click="update_number(1)">1</button>
            <button class="button number" @click="update_number(2)">2</button>
            <button class="button number" @click="update_number(3)">3</button>
            <button class="button operator" @click="math_operations('+')">+</button>
            <button class="button number zero" @click="update_number(0)">0</button>
            <button class="button decimal" @click="math_operations('.')">.</button>
            <button class="button equals" @click="update_value">=</button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'calculator_item',
    data() {
        return {
            display_value: '',
            answer_value: '',
            brackets_counter: true,
        }
    },
    methods: {
        update_value() {
            this.answer_value = '';
            this.answer_value += eval(this.display_value)

            console.log(typeof(this.answer_value))
            this.$emit('login', {
                display_value: this.display_value,
                answer_value: this.answer_value
            })
            this.display_value = '';
            this.display_value += this.answer_value;
        },
        update_expression() {
            document.getElementById('input_value').value = this.display_value
        },
        delete_value() {
            this.display_value = this.display_value.slice(0, -1);
        },
        update_number(value) {
            this.display_value += value;
            console.log(this.display_value)
        },
        clear_display() {
            this.display_value = '';
        },
        math_operations(value) {
            if (this.display_value.slice(-1) != '/' && this.display_value.slice(-1) != '*' && this.display_value.slice(-1) != '+' && this.display_value.slice(-1) != '-') {
                this.display_value += value;
            }
        },
        add_brackets() {
            if (this.brackets_counter) {
                this.display_value += '('
            } else {
                this.display_value += ')'
            }
            this.brackets_counter = !this.brackets_counter
        },
    }
}
</script>

<style scoped>
html {
    box-sizing: border-box;
    font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
    font-size: 14px;
    font-weight: 300;
}

*,
*:before,
*:after {
    box-sizing: inherit;
    margin: 0;
    padding: 0;
}

.calculator-body {
    display: grid;
    grid-template: 0.1fr 1fr / 1fr;
}

.calculator {
    background-color: #222;
    border-radius: 0 0 15px 15px;
    box-shadow: inset 0 -3px 0 rgba(0, 0, 0, 0.3);
    display: grid;
    grid-template: repeat(4, 1fr)/ repeat(4, 1fr);
    overflow: hidden;
    position: relative;
    width: 320px;
}

.display {
    background-color: grey;
    color: #fff;
    border: none;
    border-radius: 15px 15px 0 0;
    font-size: 36px;
    font-weight: 300;
    width: 320px;
    height: 70px;
    line-height: 70px;
    overflow: hidden;
    text-align: right;
    text-overflow: ellipsis;
}

.button {
    background-color: #444;
    border: none;
    color: #fff;
    cursor: pointer;
    font-size: 28px;
    height: 80px;
    outline: none;
    width: 80px;
}

.button:hover {
    background-color: #777;
}

.ac {
    background-color: #f44336;
}

.ac:hover {
    background-color: #ff6659;
}

.sign {
    background-color: #d4d4d4;
}

.sign:hover {
    background-color: #e5e5e5;
}

.percent {
    background-color: #d4d4d4;
}

.percent:hover {
    background-color: #e5e5e5;
}

.operator {
    background-color: #ff9500;
}

.operator:hover {
    background-color: #ffa94d;
}

.number {
    background-color: #333;
}

.number:hover {
    background-color: #666;
}

.zero {
    width: auto;
    grid-column: span 2;
}

.decimal {
    font-size: 48px;
}

.equals {
    background-color: #ff9500;
    color: #fff;
    font-weight: 400;
}

.equals:hover {
    background-color: #ffa94d;
}

@media screen and (max-width: 480px) {
    .calculator {
        height: 60%;
        width: 90%;
    }

    .button {
        font-size: 24px;
        height: 60px;
        width: 60px;
    }

    .display {
        font-size: 24px;
        height: 50px;
        line-height: 50px;
        padding: 0 10px;
    }

    .zero {
        width: 120px;
    }

    .decimal {
        font-size: 36px;
    }
}
</style>