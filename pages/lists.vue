<template>
    <div class="body">
        <NavBar/>
        <EditListModal :list="selectedList"/>
        <DeleteListModal :list="selectedList" @onDeleted="getAll"/>
        <div class="container"><br>
            <h1>
                My Tasks
                <ListEntryModal class="float-right" @onAdd="getAll"/>
            </h1>
            <hr>
            <br>

            <div class="tasks">
                <div class="d-flex justify-content-between flex-wrap align-items-stretch">
                    <b-card class="info mt-2" v-for="list in lists" :key="list.id">
                        <b-card-title >{{list.title}}</b-card-title><hr>
                        <b-card-text>
                            {{list.body}}
                        </b-card-text>
                        <b-card-text class="small text-muted">Last updated {{list.created_at}}</b-card-text>
                        
                        <b-button @click="onEdit(list)" variant="info" size="sm">
                            Edit <img src="~/assets/pencil.png">
                        </b-button>
                        <b-button @click="onDelete(list)" variant="danger" size="sm">
                            Delete <img src="~/assets/trash1.png">
                        </b-button>
                    </b-card>
                </div>
            </div>

        </div>
    </div>
</template>

<script>

export default {
   data(){
       return{
          
           lists:[],
           selectedList: {}
       }
   },
   methods:{
        async getAll(){
            await this.$axios.get('/api/lists')
            .then((res)=>{
                if(res.status==200) {
                    this.lists = res.data
                    console.log(this.lists)
                }
            })
        },
        onEdit(selectedList) {
            this.selectedList = selectedList;
            this.$bvModal.show('editListModal')
        },
        onDelete(selectedList) {
            this.selectedList = selectedList;
            this.$bvModal.show('deleteListModal')
        }
   },
   created(){
       this.getAll()
   }
}
</script>
<style scoped>
.body{
    height: 48rem;
    background-color: rgb(212, 220, 228);
}
.info{
    color: rgb(0, 0, 0);
}
img{
    height: 14px;
    width: 12px;
}
.tasks{
    height: 75vh;
    overflow: scroll;
}
.info{
    width: 33%;
}
</style>