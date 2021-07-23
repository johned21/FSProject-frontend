<template>
    <div>
        <b-button v-b-modal.listEntryModal variant="primary"><img src="~/assets/plus.png"> Add Task</b-button>

        <b-modal id="listEntryModal" title="List Entry" ok-title="Save" @ok="onSubmit">
            <form action="#">

                <b-form-group
                    label="Title"
                    label-for="title">
                    
                    <b-form-input id="title" v-model="list.title" trim></b-form-input>
                </b-form-group>

                <b-form-textarea
                    id="body"
                    v-model="list.body"
                    rows="8"
                    placeholder="Enter task body here..">
                        
                </b-form-textarea>
                <br>
            </form>
        </b-modal>
    </div>
</template>

<script>
export default {
    data(){
        return{
            list:{},
            
        }
    },
    methods:{
        async onSubmit(){
            this.$axios.post('/api/lists/', this.list)
            .then((res)=>{
                if(res.status==202){
                    alert('Successfully added the Task')
                    this.$emit('onAdd')
                }
            })
        }
    }
    
}
</script>

<style scoped>
img{
    height: 20px;
    width: 20px;
}
</style>