<template>
  <view class="container">
    <text class="textHeader">Vi er i uke</text>
    <text class="text-color-primary">{{ message }}</text>
    <text class="under">{{ date }}</text>
    <button class="btn" v-bind:on-press="test" title="Oppdater"/>
  </view>
</template>

<script>

export default {
  data: function () {
    return {
      message: "",
      date: ""
    }
  },
  methods: {
    test () {
      this.message = this.getWeek(); 
    },
    getWeek () {
      // Date.prototype.getWeek = function() {
      //   var onejan = new Date(this.getFullYear(),0,1);
      //   return Math.ceil((((this - onejan) / 86400000) + onejan.getDay()+1)/7);
      // }

      // var today = new Date();
      // var weekNumber = today.getWeek();
      // return weekNumber - 1; 
      var now = new Date();
      var start = new Date(now.getFullYear(), 0, 0);
      var diff = now - start;
      var oneDay = 1000 * 60 * 60 * 24;
      var day = Math.floor(diff / oneDay);
      return parseInt((day + 3) / 7); 
    },
    getDate () {
      let date = new Date();
      return date.getDate() + "." + parseInt(date.getMonth() + 1) + "." + date.getFullYear(); 
    }
  },
  mounted () {
    this.message = this.getWeek(); 
    this.date = this.getDate();
  }
}
</script>


<style>

.textHeader {
  font-size: 26px; 
}
.container {
  background-color: white;
  align-items: center; 
  justify-content: center;
  flex: 1; 
}

.under {
  padding-top: 10px;
  padding-bottom: 65px;  
}

.btn {
  position: absolute;
  bottom: 0; 
  left: 0;
  right: 0;
}

.text-color-primary {
  font-size: 110px;
}
</style>
