<template>
  <div class="holder" id="restaurants" v-if="activeItem !== null">
    <div class="item">
      <div class="item-content">
        <div class="image-holder image-holder-sm" v-if="activeItem.images !== null">
          <span v-for="(imageItem, imageIndex) in activeItem.images" :key="imageIndex">
            <img :src="imageItem.url"  v-if="imageIndex === activeImage">
          </span>
          <span class="circle-icon">
            <span v-for="(imageItem, imageIndex) in activeItem.images" :key="imageIndex" class="image-menu-holder" @click="activeImage = imageIndex">
              <img :src="imageItem.url" :class="{'active-image': activeImage === imageIndex}">
            </span>
          </span>
        </div>
        <div class="details">
          <span class="item-menu">
            <label v-for="(counter, counterIndex) in common.restaurants" :key="counterIndex" :class="{'bg-warning': active === counterIndex}" @click="setActive(counterIndex)">
              <font-awesome-icon :icon="faCocktail" v-if="counter.abbreviation === 'cocktail'"></font-awesome-icon>
              <font-awesome-icon :icon="faUtensils" v-if="counter.abbreviation === 'utensils'"></font-awesome-icon>
              <font-awesome-icon :icon="faConciergeBell" v-if="counter.abbreviation === 'concierge-bell'"></font-awesome-icon>
            </label>
          </span>
          <h3 style="margin-bottom: 10px;">
            {{activeItem.title}}
          </h3>
          <p>{{activeItem.description}}</p>
          <ul v-if="activeItem.inclusions !== null">
            <li v-for="(iItem, iIndex) in activeItem.inclusions" :key="iIndex">
              <font-awesome-icon :icon="faCheck" class="text-warning check-icon"></font-awesome-icon>
              <label>{{iItem.title}}</label>
            </li>
          </ul>
          <p v-if="active < 2">
            For inquiries, please contact us through <a :href="'tel:' + common.APP_PHONE_NUMBER" style="color: #fff;">{{common.APP_PHONE_NUMBER}}</a> or <a :href="'mailto:' + common.APP_EMAIL + '?Subject=INQUIRE'" target="_top" style="color: #fff;">{{common.APP_EMAIL}}</a>
          </p>
          <p v-if="active === 2">
            For inquiries, please dial <b>"0"</b> from your hotel room.
          </p>
        </div>
        <div class="image-holder image-holder-lg" v-if="activeItem.images !== null">
          <span v-for="(imageItem, imageIndex) in activeItem.images" :key="imageIndex">
            <img :src="imageItem.url"  v-if="imageIndex === activeImage">
          </span>
          <span class="circle-icon">
            <span v-for="(imageItem, imageIndex) in activeItem.images" :key="imageIndex" class="image-menu-holder" @click="activeImage = imageIndex">
              <img :src="imageItem.url" :class="{'active-image': activeImage === imageIndex}">
            </span>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped lang="scss">
@import "~assets/style/colors.scss";

.text-primary{
  color: $primary !important;
}

.item, .item-content{
  width: 100%;
  float: left;
  height: 100%;
}

.item-menu{
  width: 100%;
  float: left;
}

.bg-warning{
  background: $warning !important;
  color: $white !important;
}

.item-menu label:hover{
  cursor: pointer;
}

.item-menu label{
  border-radius: 50%;
  height: 50px;
  width: 50px;
  text-align: center;
  background: white;
  color: $primary;
  line-height: 50px;
  font-weight: 600;
  margin-right: 2px;
}
.holder{
  min-height: 93vh;
  width: 100%;
  float: left;
  background: $primary;
  position: relative;
}

.details{
  width: 50%;
  float: left;
  height: 100%;
  text-align: justify;
  padding-left: 50px;
  padding-right: 50px;
  padding-top: 25px;
  padding-bottom: 25px;
  color: white;
  position: relative;
}

.image-holder{
  float: left;
  height: 100%;
  width: 50%;
  overflow: hidden;
  position: relative;
}

img{
  width: 100%;
  height: 93vh;
}

.btn{
  width: 60%;
  margin-top: 0px;
}

.check-icon{
  font-size: 20px;
  margin-right: 20px;
}

ul{
  margin-top: 0px;
}
ul li{
  margin-bottom: 0px;
}

h3{
  margin-top: 10px;
  float: left;
  width: 100%;
}

h5{
  margin-top: 0px;
}

.circle-icon{
  position: absolute;
  left: 50px;
  bottom: 50px;
  z-index: 1000;
  color: white;
}

.image-menu-holder{
  width: 100px;
  height: 100px;
  overflow: hidden;
  margin-right: 10px;
}

.image-holder-lg{
  display: block;
}

.image-holder-sm{
  display: none;
}

.image-menu-holder img{
  max-height: 100px;
  max-width: 100px;
  opacity: 0.5;
}

.image-menu-holder img:hover{
  cursor: pointer;
  opacity: 1;
}

.image-menu-holder .active-image{
  opacity: 1;
}

.circle-item{
  margin-right: 5px;
}

.circle-item:hover{
  cursor: pointer;
}

@media (max-width: 992px) {
  .image-holder{
    min-height: 30vh;
    overflow-y:hidden;
    width: 100%;
  }

  img{
    width: 100%;
    height: auto;
  }
  .circle-icon{
    left: 10px;
    bottom: 10px;
  }
  .image-menu-holder{
    width: 75px;
    height: 75px;
  }

  .image-holder-lg{
    display: none;
  }

  .image-holder-sm{
    display: block;
  }

  .image-menu-holder img{
    max-width: 75px;
    max-height: 75px;
  }
  .details{
    min-height: 70vh;
    width: 100%;
    margin-top: 0px;
  }
}
</style>
<script>
import COMMON from 'src/common.js'
import { faCheck, faCircle, faUtensils, faCocktail, faConciergeBell } from '@fortawesome/free-solid-svg-icons'
export default {
  mounted(){
    setInterval(() => {
      if(this.active < COMMON.restaurants.length - 1){
        this.active++
      }else{
        this.active = 0
      }
    }, 6000)
  },
  data(){
    return {
      common: COMMON,
      faCheck: faCheck,
      faCircle: faCircle,
      faUtensils: faUtensils,
      faCocktail: faCocktail,
      faConciergeBell: faConciergeBell,
      active: 0,
      activeImage: 0
    }
  },
  computed: {
    activeItem: function (){
      return COMMON.restaurants.length > 0 ? COMMON.restaurants[this.active] : null
    }
  },
  methods: {
    openExternal(url){
      window.open(url, '_BLANK')
    },
    setActive(index){
      this.active = index
      this.activeImage = 0
    }
  }
}
</script>
