<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">
          Info: Click on a Quote to Delete it
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import QuoteGrid from './components/QuoteGrid';
  import NewQuote from './components/newQuote';
  import Header from './components/Header';

  export default {
    name: 'app',
    data() {
      return {
        quotes: [
          'Just a Quote to see something'
        ],
        maxQuotes: 10,
      }
    },
    methods: {
      newQuote(quote) {
        if (this.quotes.length >= this.maxQuotes){
          return alert('PPlease delete Quotes first!');
        }
        this.quotes.push(quote);
      },

      deleteQuote(index) {
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
