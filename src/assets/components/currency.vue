<script>
  
export default {        
    props: {
        current: {
            type: Number
        },
        money: {
            type: Object
        },
        countRub: {
            type: Function
        }, 
        countUsd: {
            type: Function
        },
        countEur: {
            type: Function
        }
    }
}

</script>

<template>
            <div class="main-block__currency">
                <div class="main-block__currency_rub dragandrop" @click="countRub()">RUB 
                    <span v-if="money.moneyEurRub != 0">{{ money.moneyEurRub }}</span>
                    <span v-if="money.moneyUsdRub != 0">{{ money.moneyUsdRub }}</span>
                </div>
                <div class="main-block__currency_usd dragandrop" @click="countUsd()">USD 
                    <span v-if="money.moneyRubUsd != 0">{{ money.moneyRubUsd }}</span>                    
                    <span v-if="money.moneyEurUsd != 0">{{ money.moneyEurUsd }}</span>
                </div>
                <div class="main-block__currency_eur dragandrop" @click="countEur()">EUR 
                    <span v-if="money.moneyRubEur != 0">{{ money.moneyRubEur }}</span>
                    <span v-if="money.moneyUsdEur != 0">{{ money.moneyUsdEur }}</span>
                </div>                 
</div>
</template>

<style scoped>

</style>
