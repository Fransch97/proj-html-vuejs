<template>
  <div class="journal container">
      <div class="container-sc">
       <div class="title d-flex">
         <div class="line"></div>
         <h5>foodie journal</h5>
         <div class="line"></div>
       </div>
         <div class="content d-flex">
           <div v-for="(journal,index) in journals" :key="`journal-${index}`" class="card-sc p-4 text-center">
             <img class="mb-4 " :src="require(`../../assets/img/${journal.img}.jpg`)" alt="">
             <h4>{{journal.title}}</h4>
             <span>{{journal.credits}}</span>
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
      journals : []
    }
  },
  methods: {
    getJournal(){
      axios.get('http://localhost:3000/journal')
      .then(r=>{  this.journals = r.data })
    }
  },
  mounted() {
    this.getJournal()
  },
}
</script>

<style lang="scss" scoped>

.journal{
  width: 100%;
  .container-sc{
    background-color: white;
    margin-top: -80px;
    position: relative;
    z-index: 100;
    padding: 30px 50px;
    box-shadow: 0px 0px 10px  -5px rgb(95, 94, 94);
    .title{ 
      align-items: center;
      .line{
        flex-grow: 1;
        border-bottom: dotted 1px lightgrey;
        height: 0;
      }
      h5{ 
        text-transform: uppercase;
        padding: 0 50px;
      }
      
    }
    .content{
      h4{
        font-family: 'Vidaloka', serif;
      }
      .card-sc{
        width: calc(100% / 3);
        img{
          width: 100%;
        }
      }
    }
  }
}
</style>