<template>
  <div id="app">
   <div class="pass text-center">
     <font-awesome-icon id="change" icon="fa-solid fa-user-ninja" @click="admin = true"/>
   </div>
   <AppAdmin v-if="admin" @close="clop" @acc="adminMode"/>
   <AppInfos v-if="acc" :visitors="visits" :admin="admin"/>
   <AppHeader :admin="acc"/>
   <AppMain :admin="acc"/>
   <AppFooter />
  </div>
</template>

<script>
import AppHeader from './components/header/AppHeader.vue';
import AppMain from './components/main/AppMain.vue';
import AppFooter from './components/footer/AppFooter.vue';
import AppAdmin from './components/admin/AppAdmin.vue';
import axios from 'axios';
import AppInfos from './components/admin/AppInfos.vue';
export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
    AppFooter,
    AppAdmin,
    AppInfos
},
  data() {
    return {
      admin: false,
      acc: false,
      visits: {},
    }
  },
  methods: {
    clop(bool){
      this.admin = bool
    },
    adminMode(bool){
      this.admin = false
      this.acc = bool
    }
  },
  mounted() {
    axios.get("http://localhost:3000/visitors")
    .then(r=>{
      this.visits = r.data
      this.visits.number += 1
      axios.put("http://localhost:3000/visitors/",this.visits)
      })
  },
}
</script>

<style lang="scss">
@import "./assets/style/global";
@import url('https://fonts.googleapis.com/css2?family=Vidaloka&display=swap');
h1{
 font-family: 'Vidaloka', serif;
}
.link{
  color: $org-color;
  background-color: white;
  width: 50px;
  height: 50px;
  font-size: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
}

html{
  background-color: white;
}

.pass{ 
  position: absolute;
  right: 0%;
  width: 50px;
  height: 50px;
  z-index: 101;
  font-size: 30px;
  &:hover #change{
    display: block;
  }
  #change{
    display: none;
  }
}
</style>
