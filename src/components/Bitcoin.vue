<template>
    <div>
        Now you can buy bitcoin for:
        <button @click="onClick">
            Bitcoin rate
        </button>
            <div v-for='currency in info' class="currency" :key="currency">

                {{currency.description}}

                <span class="lighten">
      <span v-html="currency.symbol"></span>{{ currency.rate_float | currencydecimal }}
      </span>
                <button @click="onClick1">
                    in UAH
                </button>
                <div>
                    <div v-for='rate in info1' class="currency" :key="rate">
                        {{info1[0].sale*currency.rate_float | currencydecimal}}  UAH
                        {{info1[1].sale}}

                    </div>

                </div>


            </div>



    </div>

</template>

<script>
    import axios from 'axios';
    export default {

        data: function () {
            return {
                info: {},
                info1: {}
            }
        },
        methods:{
            onClick(){
                axios
                    .get ( 'https://api.coindesk.com/v1/bpi/currentprice.json' )
                    .then ( response => (this.info = response.data.bpi) )
                },
            onClick1(){
                axios
                    .get ( 'https://api.privatbank.ua/p24api/pubinfo?json&exchange&coursid=5' )
                    .then ( response => (this.info1 = response.data) )
            },

        },
            filters: {
                currencydecimal (value) {
                    return value.toFixed(2)
                },
        }

    }
</script>

<style scoped>

</style>