<template>
  <div class="collection container">
    <div class="intro text-center">
        <div v-if="admin && !change"  @click="change = true">
            <font-awesome-icon icon="fa-solid fa-pencil" />
        </div>
        <div v-if="admin && change"  >
            <font-awesome-icon icon="fa-solid fa-check" class="px-3" @click="changeCollection"/>
            <font-awesome-icon icon="fa-solid fa-circle-xmark" @click="change = false" />
        </div>
        <h5 v-if="!change">{{collection.title}}</h5>
        <input v-model="collection.title" type="text" v-else>
        <p v-if="!change">{{collection.text}}</p>
        <input v-model="collection.text" type="text" v-else>
    </div>
    <div class="content d-flex flex-wrap text-center justify-content-between">
        <div v-for="(item, index) in collectionItems" :key="`cole-${index}`" class="collect-item my-4 pt-3 ">
            <img class="mb-4" :src="require(`../../assets/img/${item.img}.png`)"/>

            <p v-if="!changeItem">{{item.name}}</p>
            <input v-model="collectionItems[index].name" type="text" v-else>
            
            <div v-if="admin && !changeItem"  @click="changeItem = true">
            <font-awesome-icon icon="fa-solid fa-pencil" />
            </div>
            <div v-if="admin && changeItem"  >
                <font-awesome-icon icon="fa-solid fa-check" class="px-3" @click="changeCollectionItem(index)"/>
                <font-awesome-icon icon="fa-solid fa-circle-xmark" @click="changeItem = false" />
            </div>
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
            collectionItems:[],
            change: false,
            changeItem: false
        }
    },
    props:{
        admin:Boolean
    },

    methods: {
        getData(){
            axios.get("http://localhost:3000/collection")
            .then(r=>{
                this.collection = r.data
                console.log(r.data)
            })
            axios.get("http://localhost:3000/collection-items")
            .then(r=>{
                this.collectionItems = r.data
            })
        },
        changeCollection(){
            axios.put("http://localhost:3000/collection/", this.collection)
            .then(r=>{
                console.log(r.data)
            })
            alert("Fatto!")
        },
        changeCollectionItem(index){
            axios.put("http://localhost:3000/collection-items/" + index, this.collectionItems[index])
            alert("Fatto")
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
            width: calc(100% / 4 - 3%);
            font-weight: 600;
            img{
                width: 33%;
            }
            p{
                text-transform: uppercase;
                padding: 10px;
                margin: 0 5px 5px 5px;
                cursor: pointer;
                &:hover{ 
                    background-color: #fc7525;
                    color: white;
                }
            }
        }
    }
}

</style>