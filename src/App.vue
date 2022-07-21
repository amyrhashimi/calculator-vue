<template>
  <main>
  <input type="text" v-model="currentNumber">
  <div class='keys'>
    <button class='op__key' @click="clear">C</button>
    <button class='op__key' @click="opposeNumber">+/-</button>
    <button class='op__key' @click="operation('%')">%</button>
    <button class='op__key' @click="operation('/')">/</button>
    <button class='num__key' @click="addNumber('7')">7</button>
    <button class='num__key' @click="addNumber('8')">8</button>
    <button class='num__key' @click="addNumber('9')">9</button>
    <button class='op__key' @click="operation('*')">x</button>
    <button class='num__key' @click="addNumber('4')">4</button>
    <button class='num__key' @click="addNumber('5')">5</button>
    <button class='num__key' @click="addNumber('6')">6</button>
    <button class='op__key' @click="operation('-')">-</button>
    <button class='num__key' @click="addNumber('1')">1</button>
    <button class='num__key' @click="addNumber('2')">2</button>
    <button class='num__key' @click="addNumber('3')">3</button>
    <button class='op__key' @click="operation('+')">+</button>
    <span></span>
    <button class='num__key' @click="addNumber('0')">0</button>
    <button class='num__key' @click="addDot()">.</button>
    <button class='eq__key' @click="equal()">=</button>
  </div>
</main>

</template>

<script>
export default {
    name: 'App',
    data() {
        return {
            currentNumber : '',
            prevNumber : '',
            type : ''
        }
    },
    methods: {
        addNumber(Number){
            if(this.currentNumber == 0 && Number == 0 ) return;
            this.currentNumber += Number ;
        },
        addDot(){
            if(this.currentNumber.includes('.')) return;

            this.currentNumber += '.'
        },
        clear(){
            this.currentNumber = ''
        },
        opposeNumber(){
            if(parseFloat(this.currentNumber) > 0){
                this.currentNumber = '-' + this.currentNumber;
            }else{
                this.currentNumber = this.currentNumber.substring(1);
            }
        },
        operation(operation){
            this.prevNumber = this.currentNumber;
            this.currentNumber = '';
            this.type = operation;
        },
        equal(){
            switch(this.type) {
                case '+' :
                    this.currentNumber = parseFloat(this.prevNumber) + parseFloat(this.currentNumber); 
                    break;

                case '-' :
                    this.currentNumber = parseFloat(this.prevNumber) - parseFloat(this.currentNumber); 
                    break;

                case '*' :
                    this.currentNumber = parseFloat(this.prevNumber) * parseFloat(this.currentNumber); 
                    break;
                    
                case '/' :
                    this.currentNumber = parseFloat(this.prevNumber) / parseFloat(this.currentNumber); 
                    break;

                case '%' :
                    this.currentNumber = parseFloat(this.prevNumber) % parseFloat(this.currentNumber); 
                    break;
            }

            this.currentNumber = this.currentNumber.toString();
        }
  },
}
</script>
