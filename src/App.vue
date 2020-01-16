<template>
  <div class="container">
    <app-header :qoute-count="quotes.length" :max-quotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>

      </div>
    </div>
  </div>
</template>

<script>
  import Header from "./components/Header";
  import NewQuote from "./components/NewQuote";
  import QuoteGrid from "./components/QuoteGrid";

  export default {
    data: function () {
      return {
        quotes: [
          'Just a Quote to see something'
        ],
        maxQuotes: 10
      }
    },
    methods: {
      newQuote(quote) {
        if (this.quotes.length >= this.maxQuotes) {
          return alert('Please delete Quotes first!')
        }
        if (quote === '') {
          alert("Please enter Text");
        } else {
          this.quotes.push(quote)
        }
      },
      deleteQuote(index) {
        this.quotes.splice(index, 1);
      }
    },
    components: {
      appNewQuote: NewQuote,
      appQuoteGrid: QuoteGrid,
      appHeader: Header
    }
  }
</script>

<style>
</style>
