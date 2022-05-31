<template>
  <div class="jambo d-flex flex-column align-items-center justify-content-center">
      <div class="title">
          <span>Today's pick</span>
          <div v-if="admin && !change" class="modify" @click="change = true">
                <font-awesome-icon icon="fa-solid fa-pencil" />
            </div>
            <div v-if="admin && change" class="modify" @click="changedJambo(jambo.id)">
               <font-awesome-icon icon="fa-solid fa-check" />
            </div>
            <div v-if="admin && change" class="modify x" @click="change = false">
               <font-awesome-icon icon="fa-solid fa-circle-xmark" />
            </div>
          <h1 v-if="!change">{{jambo.title}}</h1>
          <input v-model="jambo.title" type="text" v-else>
          <p v-if="!change" class="date">{{jambo.date}}</p>
          <input v-model="jambo.date" type="text" v-else>
      </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
    data() {
        return {
            jambo: {},
            change: false

        };
    },
    props:{
        admin: Boolean
    },
    methods: {
        getJambo() {
            axios.get("http://localhost:3000/jambo")
                .then(r => { this.jambo = r.data; });
        },
        changedJambo(index){
        console.log(index)
        this.change = false
        axios.put("http://localhost:3000/jambo/",this.jambo)
        .then(r=>{
            console.log(r)
            this.getJambo() 
        })
    },

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
    .modify{
                position: absolute;
                right: 50%;
                bottom: 10%;
            }
            .modify.x{
                right: 45%;
            }
    .title{
        border-radius: 5px;
        background-color: white;
        padding: 40px;
        display: inline-block;
        text-align: center;
        max-width: 700px;
        position: relative;
        input{
            display: block;
            width: 400px;
        }
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