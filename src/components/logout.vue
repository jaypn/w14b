<template>
  <div>
    <button @click="logout">Log out</button>
  </div>
</template>

<script>
import axios from "axios";
import cookies from "vue-cookies";
export default {
    mounted (){
        this.logout();
    },
    name : "logout-page",
    methods: {
            login: function(){
                axios.request({
                    url: "https://reqres.in/api/login",
                    method : "DELETE",
                    
                    
                    headers:{
                        "Content-Type":"application/json"
                    },
                    data: {
                        token:cookies.get("token")
                    },
                }).then((response)=>{
                    cookies.remove("token",response.data.token);
                    this.$router.push("/login");
                }).catch((err)=>{
                    console.log(err);
                    this.error =true
                })
            }
        },
};
</script>

<style lang="scss" scoped>
</style>