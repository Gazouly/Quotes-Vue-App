<template>
    <div class="row">
        <form>
            <div class="col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                <label for="quoteBody">Quote Body</label>
                <textarea class="form-control" name="quoteBody" rows="3" v-model="quote"></textarea>
            </div>
            <div class="col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                <button class="btn btn-primary btn-lg btn-block" @click.prevent="createNewQuote">Add Quote</button>
            </div>
        </form>
    </div>
</template>

<script>
    import {eventBus} from '../main.js'
    export default {
        data() {
            return {
                quote:''
            };
        },
        methods: {
            createNewQuote() {
                eventBus.$emit('quoteAdded', this.quote);
                this.quote = "";
            }
        }
    }
</script>

<style>
    .btn.btn-primary.btn-lg {
        padding: 10px;
    }
</style>
