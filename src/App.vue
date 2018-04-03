<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAddedEvent="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @deleteQuote="quoteDeleted"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a qoute to delete it</div>
      </div>
    </div>
  </div>
</template>

<script>
  import QuoteGrid from './components/QuoteGrid.vue';
  import NewQuote from './components/NewQuote.vue';
  import Header from './components/Header.vue';    

  export default {
      data: function(){
        return {
          quotes: [
            "Just a quote"
          ],
          maxQuotes: 10
        }
      },
      methods: {
          newQuote(quote) {
            if(this.quotes.length >= this.maxQuotes){
                alert("Please delete some quotes");
                return;
              }
             this.quotes.push(quote); 
          },
          quoteDeleted(index){
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

<style lang="scss">
</style>
