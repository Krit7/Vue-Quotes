<template>
  <div class="row">
    <div v-for="(Quote,i) in Quotes" :key="Quote.id" class="panel panel-default">
      <div class="panel-body quote" @click="deleteQuote(i)">{{ Quote }}</div>
    </div>
  </div>
</template>
<script>
import { eventBus } from "../main.js";

export default {
  data: function() {
    return {
      Quotes: [],
      QuoteNo: 0
    };
  },
  methods: {
    deleteQuote(index) {
      this.QuoteNo--;
      this.Quotes.splice(index, 1);
      eventBus.$emit("QuoteNo", this.QuoteNo);
      eventBus.$emit("Quotes", this.Quotes);
    }
  },
  created() {
    eventBus.$on("Quotes", Quotes => {
      this.Quotes = Quotes;
    });
    eventBus.$on("QuoteNo", data => {
      this.QuoteNo = data;
    });
  }
};
</script>

<style scoped>
.row {
  margin-top: 10px;
  margin-bottom: 10px;
}
.quote {
  cursor: pointer;
  font-family: "Arizonia", cursive;
  font-size: 24px;
  color: #6e6e6e;
  border-style: solid;
  border-width: 0.5px;
  border-color: #cccccc;
  border-radius: 6px;
  padding: 10px 100px;
  margin: 10px;
}

.quote:hover {
  background-color: #ffe2e2;
}
</style>
