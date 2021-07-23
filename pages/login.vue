<template> 
    <div>
        <div class="bg" :style="{backgroundImage: `url(${image})`}">
        <NavBar/>

            <div class="container"><br>
                <div class="row">
                    <div class="col-md-4 offset-4 mt-3">
                        <h1>Login Form</h1>
                        <br>
                        <div class="card">
                            <b-card header="Please fill up all the fields!" style="color:white;">
                                <form action="#" @submit.prevent="onLogin">
                                    <div class="form-group" style="color:white;">
                                        <label for="email">Email</label>
                                        <input style="background-color: #0008; color:white;" type="email" v-model="creds.email" id="email" class="form-control">
                                    </div>

                                    <div class="form-group" style="color:white;">
                                        <label for="password">Password</label>
                                        <input style="background-color: #0008; color:white;" type="password" v-model="creds.password" id="password" class="form-control">
                                    </div>
            <br>
                                    <div class="form-group">
                                        <button v-if="! xhrRequest" class="btn btn-success form-control">Login</button>
                                        <button v-if="xhrRequest" class="btn btn-success form-control">
                                            <span class="spinner-border spinner-border-sm"></span> wait...
                                        </button>
                                    </div>

                                </form>
                            </b-card>
                        </div>
                        
                    </div>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
import bg from "assets/login-bg.png";
export default {
    data(){
        return{
            image: bg,
            xhrRequest: false,
            creds:{

            }
        }
    },
    methods:{
        async onLogin(){
            try{
                let v = this;

                v.xhrRequest = true;
                await this.$auth.loginWith('local', {
                    data:this.creds
                }).then((res)=>{

                }).catch((res)=>{
                    alert('Invalid credentials')
                })
            }catch(e){
                return;
            }
        }
    }
}
</script>


<style scoped>
.bg{
    height: 48rem;
    background-size:  cover;
    background-repeat:  no-repeat;
    background-attachment: fixed;
}
.card{
    background-color: #0008;
}
h1{
    text-align: center;
    color: white;
}
</style>