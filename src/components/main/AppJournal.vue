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
            <div class="img-container ">
              <div class="overlay position-absolute justify-content-center align-items-center flex-column ">
                <div class="link my-3">
                  <font-awesome-icon icon="fa-solid fa-link" />
                  </div>
                <h5>{{journal.title}}</h5>
              </div>
              <img  :src="require(`../../assets/img/${journal.img}.jpg`)" alt="">
            </div>
            <h4 class="mt-4 " v-if="!change">{{journal.title}}</h4>
            <a href="#" class="d-block mt-4 " v-if="change">
              <input v-model="journals[index].title" type="text">
            </a>
            <span  v-if="!change">{{journal.credits}}</span>
             <a href="#" class="d-block mt-4 " v-if="change">
              <input v-model="journals[index].credits" type="text">
            </a>
                  <div v-if="admin && !change" class="modify" @click="change = true">
                      <font-awesome-icon class="icon" icon="fa-solid fa-pencil" />
                  </div>
                  
                  <div v-if="admin && change" class="modify" >
                     <font-awesome-icon icon="fa-solid fa-check" @click="changedJournal(index)"/>
                     <font-awesome-icon icon="fa-solid fa-circle-xmark " class="px-4" @click="change = false" />
                  </div>
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
      journals : [],
      change: false
    }
  },
  props:{
    admin : Boolean
  },
  methods: {
    getJournal(){
      axios.get('http://localhost:3000/journal')
      .then(r=>{  this.journals = r.data })
    },
     changedJournal(index){
        console.log(index)
        axios.put("http://localhost:3000/journal/" + index ,this.journals[index])
        .then(r=>{
          console.log(index)
            console.log(r)
            this.getJournal() 
            alert("Fatto!")
        }) }
  },
  mounted() {
    this.getJournal()
  },
}
</script>

<style lang="scss" >
.modify{
  position: absolute;
  z-index: 102;
}
.modify.x{
  z-index: 102;
  left: 2%;
}
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
        .img-container{
          position: relative;
            &:hover .overlay{
              display: flex;
            }
          .overlay{
            font-family: 'Vidaloka', serif;
            height: 100%;
            width: 100%;
            color: white;
            background: linear-gradient(to bottom,  #ff5f029f, #fc7525);
            display: none;
          }
        }
        img{
          width: 100%;
        }
      }
    }
  }
}
</style>