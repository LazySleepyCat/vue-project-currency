<script>
import Count from './assets/components/count.vue'
import Currency from './assets/components/currency.vue'
export default {
    components: { Count, Currency },
    data() {
        return {
            drag: false,
            myArray: [{
                name: 'John',
                id: 0
            },
            {
                name: 'Winston',
                id: 1
            }
        ],
            current: 0,            
            result: {},
            money: {
                moneyRubEur: 0,
                moneyRubUsd: 0,
                moneyEurRub: 0,
                moneyEurUsd: 0,
                moneyUsdRub: 0,
                moneyUsdEur: 0
            }            
            
        }
    },
    methods: {
       async countRub(val) {
            val = document.querySelector('.main-block__count_value').value;
            this.current = +val;      
            let url = 'https://latest.currency-api.pages.dev/v1/currencies/rub.json';                     
            let response = await fetch(url);
            this.result = await response.json();
            let rubEur = this.result.rub.eur * this.current
            let rubUsd = this.result.rub.usd * this.current
            this.money.moneyRubEur = rubEur.toFixed(2);
            this.money.moneyRubUsd = rubUsd.toFixed(2);
            this.money.moneyUsdRub = 0;
            this.money.moneyEurRub = 0;
            this.money.moneyEurUsd = 0;
            this.money.moneyUsdEur = 0;
        },
        async countUsd(val) {
            val = document.querySelector('.main-block__count_value').value;
            this.current = +val;      
            let url = 'https://latest.currency-api.pages.dev/v1/currencies/usd.json';                     
            let response = await fetch(url);
            this.result = await response.json();
            let usdEur = this.result.usd.eur * this.current
            let UsdRub = this.result.usd.rub * this.current
            this.money.moneyUsdEur = usdEur.toFixed(2);
            this.money.moneyUsdRub = UsdRub.toFixed(2);        
            this.money.moneyEurUsd = 0;
            this.money.moneyRubUsd = 0;
            this.money.moneyRubEur = 0;
            this.money.moneyEurRub = 0;
        },
        async countEur(val) {
            val = document.querySelector('.main-block__count_value').value;
            this.current = +val;      
            let url = 'https://latest.currency-api.pages.dev/v1/currencies/eur.json';                     
            let response = await fetch(url);
            this.result = await response.json();
            let eurUsd = this.result.eur.usd * this.current
            let eurRub = this.result.eur.rub * this.current
            this.money.moneyEurUsd = eurUsd.toFixed(2);
            this.money.moneyEurRub = eurRub.toFixed(2);         
            this.money.moneyUsdRub = 0;
            this.money.moneyRubUsd = 0;
            this.money.moneyUsdEur = 0;
            this.money.moneyRubEur = 0;
        }
    } 
    } 

  

</script>

<template>

    <div class="main-block">
        <div class="main-block__wrapper">   
<Count :countRub="countRub" />

<Currency :current="current" :money="money" :countRub="countRub" :countUsd="countUsd" :countEur="countEur"/>

            </div>
        </div>

        
</template>

<style scoped>

</style>
