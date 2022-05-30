<template>
  <div class="news d-flex flex-column">
    <link rel="stylesheet" 
        href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" 
        integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" 
        crossorigin="anonymous">
    <!-- intro -->
    <div class="intro d-flex">
        
        <div class="intro-left">
          <h5 class="mb-4">{{newsIntro.title}}</h5>
          <p>{{newsIntro.text}}</p>
         
        </div>

        <div class="intro-right text-end">
          <span class="btn-sc">read our blog</span>
        </div>
    </div> 
    <!--end intro -->

    <!-- content  -->
    <div class="content d-flex">
      <!-- left  -->
       <div class="left">
          <div class="new-recipes pb-4">
            <div class="active-recipe py-4 ">
              <img :src="require(`../../assets/img/${defaultNews.img}.jpg`)" :alt="defaultNews.title">
              <div class="active-content">
                <h5 >{{defaultNews.title}}</h5>
                <span class="tags">{{defaultNews.date}}</span>
                <div class="line my-4"></div>
                <p>{{defaultNews.text}}</p>
                <div class="d-flex justify-content-between">
                  <span>Read More > </span>
                  <i>icon</i>
                </div>
              </div>
            </div>
          </div>

          <div class="all-new d-flex justify-content-between flex-wrap text-center ">
            <div v-for="news in allnews" :key="`news-${news.id}`" class="news-card pb-5 mb-5">
              <img :src="require(`../../assets/img/${news.img}.jpg`)" alt="">
              <h5>{{news.title}}</h5>
              <span class="tags">{{news.date}}</span>
            </div>
            <span class="more">load more posts</span>
          </div>

      </div>
      <!--end left  -->

      <!-- right  -->
      <div class="right">

        <!-- price -->
        <div class="lastest-recipe py-4 position-relative">
          <img src="../../assets/img/ad-bg.jpg" alt="">
          <h4 class="text-center">view our latest recipes</h4>
        </div>
        <!--end price -->

        <!-- guide  -->
        <div class="guide position-relative py-4">
          <img src="../../assets/img/singapore-featured-image-400x263.jpg" alt="">
          <h5 class="guide-title">City Guide: Singapore</h5>
          <span class="btns text-center"><font-awesome-icon class="global" icon="fa-solid fa-earth-americas" /> view all city guides</span>
        </div>
        <!-- end guide  -->

        <div class="line my-4"></div>

        <!-- social  -->
        <div class="social pt-4 pb-4">
          <div class="search mb-4">
            <i><svg xmlns="http://www.w3.org/2000/svg" width="16px" viewBox="0 0 512 512">--><path d="M500.3 443.7l-119.7-119.7c27.22-40.41 40.65-90.9 33.46-144.7C401.8 87.79 326.8 13.32 235.2 1.723C99.01-15.51-15.51 99.01 1.724 235.2c11.6 91.64 86.08 166.7 177.6 178.9c53.8 7.189 104.3-6.236 144.7-33.46l119.7 119.7c15.62 15.62 40.95 15.62 56.57 0C515.9 484.7 515.9 459.3 500.3 443.7zM79.1 208c0-70.58 57.42-128 128-128s128 57.42 128 128c0 70.58-57.42 128-128 128S79.1 278.6 79.1 208z"/></svg></i>
            <input type="search" placeholder="Search...">
          </div>

          <div class="social-advertise">
              <h5 class="py-4">Follow Us</h5>
              <div class="icons d-flex">
                <a href="#"><i class="fab fa-facebook-f d-flex justify-content-center align-items-center"></i> </a>
                <a href="#"><i class="fab fa-instagram mx-3 d-flex justify-content-center align-items-center"></i> </a>
                <a href="#"><i class="fab fa-twitter d-flex justify-content-center align-items-center"></i> </a>
                <a href="#"><i class="fab fa-youtube mx-3 d-flex justify-content-center align-items-center"></i></a>
                <a href="#"><i class="fab fa-pinterest-p d-flex justify-content-center align-items-center"></i></a>
              </div>
          </div>
        </div>
        <!--end social  -->

        <!-- posts table  -->
        <div class="posts-table pt-4 pb-4">

          <div class="posts-evidence d-flex text-center pb-4">
            <h6 class="active">Popular</h6>
            <h6>Recent</h6>
          </div>

          <!-- pop -->
          <ul v-if="postsTable === 'pop' ? 'active':''" >
            <li class="py-3" v-for="(pop, index) in popPosts" :key="`pop-${index}`">
              <a class="d-flex align-items-center" href="#">
                <img :src="require(`../../assets/img/${pop.img}.jpg`)" :alt="pop.title">
                <div class="pop-text">
                  <p>{{pop.title}}</p>
                  <span>{{pop.date}}</span>
                </div>
              </a>
            </li>
          </ul>
          <!--end pop -->
          
          <!-- recent -->
          <ul v-if="postsTable === 'recent' ? 'active':''">
            <li>
              <a href="#">
                <img src="" alt="">
              </a>
            </li>
          </ul>
          <!-- end recent -->

        </div>
        <!--end posts table   -->

<blockquote class="twitter-tweet" data-lang="it" data-theme="light"><p lang="en" dir="ltr">Sunsets don&#39;t get much better than this one over <a href="https://twitter.com/GrandTetonNPS?ref_src=twsrc%5Etfw">@GrandTetonNPS</a>. <a href="https://twitter.com/hashtag/nature?src=hash&amp;ref_src=twsrc%5Etfw">#nature</a> <a href="https://twitter.com/hashtag/sunset?src=hash&amp;ref_src=twsrc%5Etfw">#sunset</a> <a href="http://t.co/YuKy2rcjyU">pic.twitter.com/YuKy2rcjyU</a></p>&mdash; US Department of the Interior (@Interior) <a href="https://twitter.com/Interior/status/463440424141459456?ref_src=twsrc%5Etfw">5 maggio 2014</a></blockquote>  
      </div>
      <!--end right  -->
    </div>
    <!--end content  -->
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      newsIntro: {},
      newItems: [],
      newsDefault: 0,
      newsDefaultObj: {},
      postsTable: "pop",
      popPosts: [
        {
          img : "single-post-img3-66x66",
          title: "Food Corner: Top Japanese restaurants for Sushi",
          date: "march 25th, 2019",
          clicks : 127
        },
        {
          img : "singapore-featured-image-66x66",
          title: "City Guide: Singapore",
          date: "February 27th, 2019",
          clicks : 126
        },
        {
          img : "slide1-bg-66x66",
          title: "6 Nutritional Tips to Hel Burn Body Fat",
          date: "February 28th, 2019",
          clicks: 125
        }
      ]
      
    }
  },
  computed:{
    defaultNews(){
      return this.newItems[this.newsDefault]
      },
      allnews(){
        return this.newItems.filter((obj, index) => !(index === this.newsDefault))
      }
  },
    methods: {
      getData(){
        axios.get("http://localhost:3000/news-left")
          .then(r=>{ 
            this.newsIntro  = r.data[0]
            this.newItems  = r.data[1]
            })
          
        },
        
    },

    mounted() {
      this.getData()
    },
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/global";
@import "../../assets/style/mainSectionNews";
</style>
