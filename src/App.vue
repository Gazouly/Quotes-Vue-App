<template>
    <div class="container">
        <br>
        <br>
        <app-header :quotesCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Click on a quote to delete it!
                </div>
            </div>
        </div>
        <app-new-quote></app-new-quote>
        <app-quote-grid :quotes="quotes"></app-quote-grid>
        <div class="row">
            <div v-if="showSuccess" class="col-sm-12 text-center">
                <div class="alert alert-success">
                    You've just added a new quote!
                </div>
            </div>
            <div v-if="showDanger" class="col-sm-12 text-center">
                <div class="alert alert-danger">
                    You've just deleted a new quote!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue'
    import NewQuote from './components/NewQuote.vue'
    import Header from './components/Header.vue'
    import {
        eventBus
    } from './main.js'
    export default {
        data() {
            return {
                quotes: ["hey"],
                maxQuotes: 10,
                showSuccess: false,
                showDanger: false
            };
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        },
        created() {
            eventBus.$on('quoteAdded', (quote) => {
                this.quotes.push(quote);
                this.showSuccess = true;
                setTimeout(() => {
                    this.showSuccess = false;
                }, 2000);
            });
            eventBus.$on('deleteQuote', (i) => {
                this.quotes.splice(i, 1);
                this.showDanger = true;
                setTimeout(() => {
                    this.showDanger = false;
                }, 2000);
            });
        }
    }
</script>

<style>
    
</style>
