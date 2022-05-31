<template>
  <div class="admin">
      <div class="close btn-dark d-inline px-2 py-1 text-end" @click="$emit('close', false)">X</div>
      <h1 class="text-center">Admin</h1>
      <form action="" class="d-flex flex-column px-5">
          <label for="">Name</label>
          <input v-model="nick" type="text"  placeholder="name">
          <label for="">Password</label>
          <input v-model="pw" type="password">
          <button class="btn btn-dark my-3" @click="getAcc">Enter</button>
      </form>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            nick: "",
            pw: "",
            admin: false
        }
    },
    
    methods: {
        getAcc(e){
            e.preventDefault();
            const nickname = this.nick
            const password = this.pw
            axios.get("http://localhost:3000/admin")
            .then(r=>{
                const data = r.data
                if(data.name === nickname.toLowerCase().trim() && data.password === password.toLowerCase().trim() ){
                    this.top()
                    alert("Benvenuto Admin!")
                }else{
                    alert("I dati inseriti non sono correti")
                }
            })
        },
        top(){
            this.$emit('acc', true)
            this.admin = true
        }
    },
}
</script>

<style lang="scss">
.admin{
    background-color: white;
    position: fixed;
    z-index: 101;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    height: 30vh;
    width: 30vw;
    border: solid 2px black;
    .close{
        position: absolute;
        right:0 ;
    }
    
}

</style>