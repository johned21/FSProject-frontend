<template>
    <div>

        <b-modal id="deleteListModal" title="Delete Task" ok-title="Delete" @ok="onDelete" ok-variant="danger">
            Are You Sure about deleting this Task?<br><br>
            <h2>{{list.title}}</h2> 
            <h5>- {{list.body}}</h5>
        </b-modal>
    </div>
</template>

<script>
export default {
    props: {
        list: {}
    },
    methods: {
        async onDelete(){
            this.$axios.delete('/api/lists/' + this.list.id)
            .then((res)=>{
                if(res.status==202) {
                    alert('Task is deleted successfully')
                    this.$emit('onDeleted')
                }
            })
        }
    }
}
</script>