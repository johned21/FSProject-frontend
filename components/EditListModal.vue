<template>
    <div>

        <b-modal id="editListModal" title="Task Entry" ok-title="Save" @ok="onSubmit">
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

            </form>
        </b-modal>
    </div>
</template>

<script>
export default {
    props: {
        list: {}
    },
    data(){
        return{
            list:{},
            
        }
    },
    methods: {
        async onSubmit(){
            this.$axios.put('/api/lists/' + this.list.id, this.list)
            .then((res)=>{
                if(res.status==202) {
                    alert('Update Succesful!!')
                }
            })
            .catch((err)=>{
                alert(err.message)
            })
        }
    }
}
</script>