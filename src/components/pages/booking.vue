<template>
  <div class="incre-container">
    <subscribe class="subscribe"></subscribe>
    <div class="form-container">
      <span class="margin-div">
      </span>
      <date-picker
        type="date"
        v-model="checkInDate"
        :disabled-date="beforeToday"
        placeholder="Check in"
        value-type="format"
        :default-value="new Date()"></date-picker>

        <date-picker
        type="date"
        :disabled-date="beforeToday"
        placeholder="Check out"
        value-type="format"
        v-model="checkOutDate"
        :default-value="new Date()"></date-picker>

        <select class="form-control" placeholder="Select Adult" v-model="adult">
          <option value="" selected="selected">Select Adult</option>
          <option v-for="(item, index) in 20" :key="index" :value="item">{{item}}</option>
        </select>


        <select class="form-control" placeholder="Select Adult" v-model="children">
          <option value="" selected="selected">Select Children</option>
          <option v-for="(item, index) in 20" :key="index" :value="item">{{item}}</option>
        </select>

        <button class="btn btn-warning" @click="openExternal(common.booking_link)">BOOK A ROOM</button>
    </div>
    <img :src="common.APP_HEADER_BACKGROUND" align="right">
  </div>
</template>
<style scoped lang="scss">
@import "~assets/style/colors.scss";
  .incre-container{
    min-height: 73vh;
    float: left;
    width: 100%;
    position: relative;
    overflow: hidden;
  }

  img{
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    width: 100%;
  }
  .form-container{
    width: 100%;
    float: left;
    min-height: $height;
    background: rgba(255, 255, 255, 0.5);
    z-index: 1000;
    padding-top: 2vh;
    padding-bottom: 2vh;
    position: absolute;
    bottom: 0;
  }

  .form-control{
    margin-top: 2vh !important;
    margin-bottom: 1vh !important;
    width: 14% !important;
    float: left !important;
    margin-left: 1% !important;
  }

  .btn{
    width: 20% !important;
    margin-top: 2vh !important;
    margin-left: 1% !important;
  }

  .margin-div{
    width: 9%;
    float: left;
    height: 10vh;
  }

@media screen and (max-width: 992px){
  .subscribe{
    display: none;
  }

  img{
    width: 100%;
    height: 100%;
  }

  .form-control{
    width: 48% !important;
  }

  .btn{
    width: 98% !important;
    margin-bottom: 25px !important;
  }

  .margin-div{
    width: 0px;
  }
}
</style>
<script>
import DatePicker from 'vue2-datepicker'
import COMMON from 'src/common.js'
import 'vue2-datepicker/index.css'
import Subscribe from 'src/components/generic/subscribe.vue'
export default {
  mounted(){
  },
  data(){
    return{
      common: COMMON,
      checkInDate: null,
      checkOutDate: null,
      adult: '',
      children: ''
    }
  },
  components: {
    DatePicker,
    Subscribe
  },
  methods: {
    beforeToday(date){
      return date < new Date()
    },
    openExternal(url){
      window.open(url, '_BLANK')
    }
  }
}
</script>
