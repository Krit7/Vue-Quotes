<template>
  <div class="container col-sm-12">
    <div class="container addQuote">
      <h5>Quote</h5>
      <textarea class="form-control" rows="3" placeholder="Write here..." v-model="Quote"></textarea>
      <div class="btn-div">
        <button class="btn btn-primary" @click="addQuote()">Add Quote</button>
      </div>
    </div>
  </div>
</template>
<script>
import { eventBus } from "../main.js";

export default {
  data: function() {
    return {
      Quote: "",
      Quotes: [],
      QuoteNo: 0
    };
  },
  methods: {
    addQuote() {
      if (this.QuoteNo < 10) {
        this.Quotes.push(this.Quote);
        this.QuoteNo = this.Quotes.length;
        this.Quote = "";
        eventBus.$emit('QuoteNo',this.QuoteNo);
        eventBus.$emit('Quotes',this.Quotes);
      } else {
        alert("Too many Quotes! Delete somebefore adding new ones");
      }
    }
  },
  created(){
      eventBus.$on('QuoteNo',(data)=>{
          this.Progress=data;
      });
      eventBus.$on("Quotes", Quotes => {
      this.Quotes = Quotes;
    });
  }
};
</script>

<style scoped>
.addQuote {
  margin-top: 30px;
  padding-left: 25%;
  padding-right: 25%;
}
h5 {
  font-weight: bold;
}
.btn-div {
  text-align: center;
  margin: 15px;
}
</style>