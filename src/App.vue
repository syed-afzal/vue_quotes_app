<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxNoOfQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">
          Info: Click on a Quote to delete it
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid";
import NewQuote from "./components/NewQuote";
import Header from "./components/Header";

export default {
  data () {
    return {
      maxNoOfQuotes: 10,
      quotes: [
        'Just a Quote to see something'
      ]
    }
  },
  methods: {
    newQuote: function (quote) {
      if(this.quotes.length >= this.maxNoOfQuotes){
        return alert('Limit reached: You should delete firts some quotes')
      }
      this.quotes.push(quote)
    },
    deleteQuote: function (index) {
      this.quotes.splice(index, 1)
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
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
