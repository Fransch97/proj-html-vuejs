<template>
  <div class="rights py-4 text-center">
      <span v-for="(right, index) in rights" :key="index">&copy; {{right}}</span>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            rights: []
        }
    },
    methods: {
        getRights(){
            axios.get("http://localhost:3000/rights")
            .then(r=>{this.rights = r.data})
        }
    },
    mounted() {
        this.getRights()
    },
}
</script>

<style lang="scss" >
span{
    font-size: 12px;
    color: #68615a;
}

</style>