<template>
  <div class="jambo d-flex flex-column align-items-center justify-content-center">
      <div class="title">
          <span>Today's pick</span>
          <h1>{{jambo.title}}</h1>
          <p class="date">{{jambo.date}}</p>
      </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
    data() {
        return {
            jambo: {}
        };
    },
    methods: {
        getJambo() {
            axios.get("http://localhost:3000/jambo")
                .then(r => { this.jambo = r.data; });
        }
    },
    mounted() {
        this.getJambo();
    },
    
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/global";
.jambo{
    height: 650px;
    background-image: url(../../assets/img/single-post-img3-1200x790.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    padding: 100px;
    .title{
        border-radius: 10px;
        background-color: white;
        padding: 40px;
        display: inline-block;
        text-align: center;
        max-width: 700px;
        position: relative;
        h1{
            font-size: 40px;
            font-family: Arial, Helvetica, sans-serif
        }
        span{ 
            text-transform: uppercase;
            background-color:$org-color ;
            position: absolute;
            top: -10%;
            right: 50%;
            transform: translateX(50%);
            padding: 8px 20px;
            border-radius: 10px;
            font-weight: bold;
            color: white;
            box-shadow:0px 10px 50px rgb(115, 114, 114);
        }
        .date{
            font-weight: bold;
            color: lightgrey;
        }
    }
}

</style>