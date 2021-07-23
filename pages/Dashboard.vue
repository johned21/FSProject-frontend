<template>
    <div>
        <NavBar/>
        <div class="jumbotron" :style="{backgroundImage: `url(${image})`}">
        </div>
        <div class="container">
            <div>
                <img src="~/assets/profile.png">

                <div class="prof">
                    <h3><strong>{{$auth.user.fullname}}</strong></h3>
                    <h5>{{$auth.user.email}}</h5>
                </div>
                
            </div>
            <a href="/lists" class="btn btn-success float-right btn-sm" style="margin-top:-40px;">Go to My Tasks</a>
            <hr>
        </div>    
        
    </div>
</template>
<script>
import bg from "assets/jumbo-bg.png";
export default {
    data(){
        return{
            image: bg,
            
        }
    },
}
</script>
<style scoped>
th{
    font-size: 18px;
}

.pp{
    height: 220px;
    width: 220px;
    margin-left: 12%;
    margin-right: 30%;
}
.row{
    margin-top: 2%;
    margin-left: 2%;
    height: 32rem;
    width: 70rem;

}
.jumbotron{
    height: 22rem;
    background-size:  cover;
    background-repeat:  no-repeat;;
}

h3{
    
    font-size: 23px;
}

h5{
   
    font-size: 14px;
}

.prof{
    margin-top: -7rem;
    margin-left: 18rem;
}

hr{
    margin-top: 3rem;
}

img{
    height: 230px;
    width: 230px;
}
.container{
    margin-top: -140px;
}
</style>