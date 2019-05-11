<template>
  <div class="container">
    <QuoteBar></QuoteBar>
    <AddQuote></AddQuote>
    <DisplayQuotes></DisplayQuotes>
    <QuoteInfo></QuoteInfo>  
  </div>
</template>

<script>
import QuoteBar from './components/QuoteBar.vue';
import AddQuote from './components/AddQuote.vue';
import DisplayQuotes from './components/DisplayQuotes.vue';
import QuoteInfo from './components/Info.vue';

export default {
  components :{
    QuoteBar : QuoteBar,
    AddQuote: AddQuote,
    DisplayQuotes: DisplayQuotes,
    QuoteInfo:QuoteInfo
  }
};
</script>

<style>
</style>
