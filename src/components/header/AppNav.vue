<template>
  <nav class="my-2 container">
      <ul class="d-flex justify-content-center">
        <li 
            v-for="(link, index) in links" 
            :key="`link-${index}`" 
            :class=" activeDefault === index ? 'active' : ''"
            @click="page(index, link)"
            >
            {{link}}
        </li>
        <li>
            <svg xmlns="http://www.w3.org/2000/svg" width="16px" viewBox="0 0 512 512">--><path d="M500.3 443.7l-119.7-119.7c27.22-40.41 40.65-90.9 33.46-144.7C401.8 87.79 326.8 13.32 235.2 1.723C99.01-15.51-15.51 99.01 1.724 235.2c11.6 91.64 86.08 166.7 177.6 178.9c53.8 7.189 104.3-6.236 144.7-33.46l119.7 119.7c15.62 15.62 40.95 15.62 56.57 0C515.9 484.7 515.9 459.3 500.3 443.7zM79.1 208c0-70.58 57.42-128 128-128s128 57.42 128 128c0 70.58-57.42 128-128 128S79.1 278.6 79.1 208z"/></svg>
        </li>
      </ul>
  </nav>
</template>

<script>
import axios from "axios"
export default {
data() {
    return {
        links : [],
        activeDefault : 0
    }
},
methods: {
    getLinks(){
        axios.get("http://localhost:3000/navLinks")
        .then(r=>{this.links = r.data})
    },
    page(param,name){
        this.activeDefault = param
        this.$emit('onPage', name)
    }
},
mounted() {
    this.getLinks()
},
}
</script>

<style lang="scss">
@import "../../assets/style/global";
nav{
    ul{ 
        li{ 
            list-style: none;
            margin: 0 4%;
            font-family: $font-cat;  
             padding-bottom: 6px;
            text-transform: capitalize;
            cursor: pointer;
        }
           
            .active{
                border-bottom: $org-color solid 3px;
                font-family: $font-cat;   
            }
    }
}
</style>