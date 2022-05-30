<template>
  <div class="collection container">
    <div class="intro text-center">
        <h5>{{collection.title}}</h5>
        <p>{{collection.text}}</p>
    </div>
    <div class="content d-flex flex-wrap text-center justify-content-between">
        <div v-for="(item, index) in collectionItems" :key="`cole-${index}`" class="collect-item my-4 pt-3 ">
            <img class="mb-4" :src="require(`../../assets/img/${item.img}.png`)"/>
            <p>{{item.name}}</p>
            
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            collection:{},
            collectionItems:[]
        }
    },

    methods: {
        getData(){
            axios.get("http://localhost:3000/collection")
            .then(r=>{
                this.collection = r.data[0]
                this.collectionItems = r.data[1]
            })
        }
    },

    mounted() {
        this.getData()
    },
}
</script>

<style lang="scss" scoped>
.collection{ 
    padding-bottom: 100px;
    .intro{ 
        width: 50%;
        margin: auto;
        padding: 50px;
        h5{
        text-transform: uppercase;
        }
    }
    .content{
        .collect-item{
            background-color: white ;
            width: calc(100% / 4 - 50px);
            img{
                width: 33%;
            }
            p{
                text-transform: uppercase;
            }
        }
    }
}

</style>