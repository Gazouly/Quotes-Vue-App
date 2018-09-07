<template>
    <div class="row">
    
        <app-quote v-for="(quote, i) in quotes" :key="quote.id" @click.native="deleteQuote(i)">{{quote}}</app-quote>
    
    </div>
</template>

<script>
    import Quote from './Quote.vue';
import { eventBus } from '../main';
    
    export default {
    
        props: ['quotes'],
    
        components: {
    
            appQuote: Quote
    
        },
        methods: {
            deleteQuote(i) {
                eventBus.$emit('deleteQuote', i);
            }
        }
    
    }
</script>

<style>
    
</style>
