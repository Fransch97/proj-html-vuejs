<template>
  <div class="infos text-center d-flex flex-column justify-content-center">
      <div><h5>Visitatori totali: {{visitors.number}} <font-awesome-icon icon="fa-solid fa-eye" /></h5> </div>
      <div><h5>Post totali: {{posts}} <font-awesome-icon icon="fa-solid fa-sheet-plastic" /></h5></div>
      <div><h5>Like totali: {{likes}}<font-awesome-icon icon="fa-solid fa-thumbs-up" /></h5></div>
      
  </div>
</template>

<script>
import axios from 'axios'
export default {

    data() {
        return {
            posts: 0,
            data:[],
            likes: 0
        }
    },
    props:{
        visitors: Object,
    },
    methods:{
        getData(){
            axios.get("http://localhost:3000/news-left-items")
            .then((result) => {
             this.data = result.data
             this.posts = this.data.length
             
             this.data.forEach(el=>{
                 this.likes += el.clicks
             })
            })
        }
    },
    mounted() {
        this.getData()
    },
}
</script>

<style lang="scss">
.infos{
    width: 300px;
    height: 200px;
    border: 2px solid black;
    background-color: white;
    background-image: url("../../assets/img/subscribe-sec-bg.png");
    background-size: 90%;
    position: fixed;
    right: 0;
    top: 20%;
    z-index: 104;
    
}
</style>