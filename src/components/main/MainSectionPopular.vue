<template>
  <div class="popular ">
    <div class="intro text-center">
      <h5>{{pop.title}}</h5>
      <p>{{pop.text}}</p>
    </div>
    <div class="content d-flex">
      <div class="active-card py-3 px-3">
        <img :src="require(`../../assets/img/${activeCardObj.img}.jpg`)" alt="">
        <div class="active-content">
          <h5>{{activeCardObj.title}}</h5>
          <span class="tags">{{activeCardObj.tags}}</span>
          <div class="line my-4"></div>
          <p>{{activeCardObj.text}}</p>
          <span class="btn-sc">learn more</span>
        </div>
      </div>
      <div class="items d-flex flex-wrap">
        <div
          v-for="(item, index) in filterItems"
          :key="`card-pop${index}`" 
          class="item py-3 px-3">
          
          <img  class="" :src="require(`../../assets/img/${item.img}.jpg`)" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
  data() {
    return {
      pop:{},
      items:[],
      activeCard: 0,
      activeCardObj:{}
      
    }
  },
  computed:{
    filterItems(){
      return this.items.filter((obj,
       index)=> !(this.activeCard === index))
    }
  },

    methods: {
        getData(){
          axios.get("http://localhost:3000/popular-items")
          .then(r=>{ 
            this.items  = r.data
            this.activeCardObj = r.data[this.activeCard]
            })
          
          axios.get("http://localhost:3000/popular")
          .then(r=>{ this.pop  = r.data})

        },
        
    },

    mounted() {
      this.getData()
    },
}
</script>

<style lang="scss">
@import "../../assets/style/global";
.popular{
  padding: 100px 0px;

  .intro{ 
    width: 60%;
    margin: auto;
    padding: 50px;
    h5{
      text-transform: uppercase;
    }
  }

  .content{
    .active-card{
      width: 50%;
        display: flex;
        flex-direction: column;
      .active-content{
        background-color: white;
        padding: 40px;
        flex-grow: 1;
        .tags{
          font-family: $font-cat;
          font-size: 14px;
        }
        .line{
        flex-grow: 1;
        border-bottom: dotted 1px lightgrey;
        height: 0;
        }
        .btn-sc{
          text-transform: uppercase;
          background-color: $org-color;
          color: white;
          font-size: 12px;
          font-family: $font-cat;
          font-weight: bold;
          padding: 8px 20px;
          border-radius: 3px;
        }
      }
      img{
        width: 100%;
      }
    }
    .items{
      max-width: 50%;
      .item{
        width: 50%;
        img{
          width: 100%;
        }
      }
      }

  }
}

</style>