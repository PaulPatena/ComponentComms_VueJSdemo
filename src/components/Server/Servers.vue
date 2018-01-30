<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <span v-for="serv in servers" v-bind:key=serv.id>
                <serv-comp v-bind:server="serv"></serv-comp>
            </span>           
        </ul>
    </div>
</template>

<script>
import ServerComponent from './ServerComponent.vue'
export default {
    data: function() {
        return {
            servers: [ 
                {id: 1, status: 'Normal'},
                {id: 2, status: 'Critical'},
                {id: 3, status: 'Unknown'},
                {id: 4, status: 'Normal'},
            ]
        }
    },
    components: {
        'serv-comp': ServerComponent
    }
}
</script>

<style>

</style>
