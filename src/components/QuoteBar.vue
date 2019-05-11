<template>
  <div class="Bar"> 
    <h2>Quotes Added</h2>
    <div class="progress">
      <div class="progress-bar" :style="{width:(Progress)*10+'%'}">{{Progress}}/10</div>
    </div>
  </div>
</template>

<script>

import {eventBus} from '../main.js';

export default {
  data: function() {
    return {
      Progress : 0
    };
  },
  created(){
      eventBus.$on('QuoteNo',(data)=>{
          this.Progress=data;
      });
  }
};
</script>

<style scoped>

.Bar{
    margin-top: 50px;
    margin-bottom: 25px;
}
h2{
    font-weight: 600;
}
.progress{
    margin-top: 25px;
    /* margin-bottom: 15px; */
    height: 25px;
}
</style>
