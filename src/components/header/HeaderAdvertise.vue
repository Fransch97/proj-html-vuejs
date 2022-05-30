<template>
  <div class="header-ads my-2 container">
      <div class="advertise d-flex justify-content-between">
          <link rel="stylesheet" 
        href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" 
        integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" 
        crossorigin="anonymous">
          <div class="contact-business ">
              <a class="mx-3" href="#">Donwload App <span id="ios">IOS</span></a>
              <a href="#">Advertise with us</a>
          </div>
          <div class="social-advertise">
              <a href="#"><i class="fab fa-facebook-f mx-3"></i> </a>
              <a href="#"><i class="fab fa-instagram mx-3"></i> </a>
              <a href="#"><i class="fab fa-twitter mx-3"></i> </a>
              <a href="#"><i class="fab fa-youtube mx-3"></i></a>
          </div>
      </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" >
@import "../../assets/style/global";
 .header-ads{
     color: #9d9994 ;
     font-family: $font-cat;
     a{
        color: #9d9994 ;
     }
     .contact-business{ 
         a{ 
             font-size: 12px;
             #ios{
                 background-color: #fc7525;
                 color: white;
                 font-size: 8px;
                 padding: 1px 4px;
                 border-radius: 3px;
             }
        }
     }
 }
</style>
