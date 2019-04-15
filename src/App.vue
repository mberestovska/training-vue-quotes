<template>
    <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
        <div class="col-sm-12 text-center">
            <div class="alert alert-info">
                Info: Click on a Quote to delete it!
            </div>
        </div>
    </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/quoteGrid.vue';
    import NewQuote from './components/newQuote.vue';
    import Header from './components/header.vue';
    export default {
        data: function (){
            return {
                quotes: [
                    'This is the first quote'
                ], 
                maxQuotes: 10
            }
        },
        methods: {
            newQuote(quote){
                if (this.quotes.length >= this.maxQuotes){
                    return alert('Please delete some quote!')
                }
                this.quotes.push(quote);
            },
            deleteQuote(index){
                this.quotes.splice(index, 1);
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
