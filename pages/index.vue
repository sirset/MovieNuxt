<template>
  <v-row justify="center" align="center">
    <v-col cols="12" >
      <swiper class="swiper" :options="swiperOption">
        <swiper-slide>Slide 1</swiper-slide>
        <swiper-slide>Slide 2</swiper-slide>
        <swiper-slide>Slide 3</swiper-slide>
        <swiper-slide>Slide 4</swiper-slide>
        <swiper-slide>Slide 5</swiper-slide>
        <swiper-slide>Slide 6</swiper-slide>
        <swiper-slide>Slide 7</swiper-slide>
        <swiper-slide>Slide 8</swiper-slide>
        <swiper-slide>Slide 9</swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
        <div class="swiper-button-prev" slot="button-prev"></div>
        <div class="swiper-button-next" slot="button-next"></div>
      </swiper>
    </v-col>
    
    <v-col cols="12" sm="4" md="5">
      <v-card>
        <v-card-title>
          Filter By
        </v-card-title>
        <v-divider></v-divider>
        <v-card-text>
          <v-text-field 
            v-model="genmovie"
            label="Star typing to search..."
            background-color="white"
            color="black"
            append-icon="mdi-magnify"
            @click:append="searchgen"
            outlined          
            clearable
            rounded
            >
          </v-text-field>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col cols="12" sm="8" md="7">
      lado izquierdo
    </v-col>
  </v-row>
</template>

<script>
  import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
  import 'swiper/css/swiper.css'  

  export default {
    components: {
      Swiper,
      SwiperSlide
    },
    data() {
      return {
        genmovie:"",
        veuxtest: this.$store.state.keyapimovie,
        swiperOption: {
          slidesPerView: 3,
          spaceBetween: 10,
          slidesPerGroup: 1,
          loop: true,
          loopFillGroupWithBlank: true,
          pagination: {
            el: '.swiper-pagination',
            clickable: true
          },
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
          }
        }
      }
    },
    methods:{
      searchgen(){
        console.log(this.veuxtest)
      }
    }
  }
</script>

<style >
  .swiper {
    height: 300px;
    width: 100%;    
  }
  .swiper-slide {
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      font-weight: bold;
      font-size: font-size-huge * 2;
      background-color: white;
    }
</style>