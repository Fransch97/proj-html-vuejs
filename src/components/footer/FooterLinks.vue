<template>
  <div class="connections py-5  ">
        <div class="container d-flex justify-content-center">
            <ul class="border-sc">
          <li class="py-4">
              <img src="../../assets/img/avada-food-logo-mob-2x.png" alt="">
          </li>
          <li>
            <div class="social-advertise py-4">
              <a href="#"><i class="fab fa-facebook-f "></i> </a>
              <a href="#"><i class="fab fa-instagram mx-3"></i> </a>
              <a href="#"><i class="fab fa-twitter"></i> </a>
              <a href="#"><i class="fab fa-youtube mx-3"></i></a>
            </div>
          </li>
      </ul>

    <ul class="border-sc">
        <li 
        class="cap py-2"
        v-for="(link, index) in links" 
        :key="`link-${index}`" 
        >
            {{link}}
        </li>
    </ul>

    <ul class="border-sc">
        <li><p class="title">contact</p></li>
        <li class="py-2">
            <i class="fa-solid fa-location-dot"></i>
            <span>775 New York Ave, Brooklyn, Kings, New York 11203</span>
        </li>
        <li class="py-2">
            <i class="fa-solid fa-phone-flip"></i>
            <span>+ 0100-505-0000</span>
        </li>
        <li class="py-2">
            <i class="fa-solid fa-envelope"></i>
            <span>info@your-donain.com</span>
        </li>
    </ul>

    <ul>
        <li>
            <p class="title"> get our app</p>
        </li>
        <li class="py-3">
            <img src="../../assets/img/download-android.png" alt="">
        </li>
        <li>
            <img src="../../assets/img/download-app-store.png" alt="">
        </li>
        
    </ul>
        </div>
  </div>
</template>

<script>
import axios from 'axios'
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
            .then(r=>{this.links = r.data; this.links.splice(0,1)})
        }
    },
    mounted() {
        this.getLinks()
    }
}
</script>

<style lang="scss">
@import "../../assets/style/global";
.connections{ 
    background-color: white;
    ul{
        img{
            width: 100%;
        }
        list-style: none;
        width: calc(100% / 4);
        padding: 0 60px;
        .title{ 
            text-transform: uppercase;
            color: $org-color;

        }
        .cap{ 
            text-transform: capitalize;
            font-weight: 600;
        }
        i{
            font-size: 20px;
            color: #afafaf;
        }

    }
        .border-sc{
            border-right: 1px dotted #afafaf;
        }
}

</style>