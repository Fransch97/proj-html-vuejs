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
        border-radius: 5px;
        background-color: white;
        padding: 40px;
        display: inline-block;
        text-align: center;
        max-width: 700px;
        position: relative;
        h1{
            font-size: 40px;
            font-family: 'Vidaloka', serif;
        }
        span{ 
            text-transform: uppercase;
            background-color:$org-color ;
            position: absolute;
            top: -10%;
            right: 50%;
            transform: translateX(50%);
            padding: 10px 20px;
            border-radius: 5px;
            font-weight: bold;
            color: white;
            box-shadow: 0px 0px 10px  -5px rgb(95, 94, 94);

        }
        .date{
            font-weight: bold;
            color: lightgrey;
        }
    }
}

</style>