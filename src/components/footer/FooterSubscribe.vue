<template>
  <div class="subscribe d-flex justify-content-center align-items-center text-center">
      <div class="content">
            <h1 class="py-3">Subscribe <a class="org">&</a> Recive A Free eBook</h1>
            <p>Aliquam volutpat. Ut quis ligula a magna bladit finibus. Suspendisse maximus lacus non nunc lacinia lobortis.</p>

            <div class="subscripton d-flex align-items-center py-4">
                <input type="email" placeholder="Insert your email...*">
                <span id="subscribe-btn" class="mx-3">subscribe</span>
            </div>

            <span>Cras porttitor pellentesque sem eu pertium.</span>
      </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
@import "../../assets/style/global";
.subscribe{
    padding: 200px 0;
    background-image: url("../../assets/img/subscribe-sec-bg.png");
    background-color: white;
    background-size: cover;
    p{ 
        width: 95%;
    }
    input{ 
        width: 100%;
        padding: 10px 20px;
        border-radius: 5px;
        border-width: 0;
        border: solid 2px lightgrey;
        border-radius: 5px;
    }
    #subscribe-btn{
        text-transform: uppercase;
        background-color: $org-color;
        color: white;
        font-family: $font-cat;
        font-weight: bold;
        padding: 12px 40px;
        border-radius: 2px;
    }
    span{
        color: #76777a;
        font-size: 14px;
        font-weight: 500;
    }
    .subscripton{
        width: 80%;
        margin: auto;
    }
    .org{ 
        color: $org-color;
    }
}

</style>