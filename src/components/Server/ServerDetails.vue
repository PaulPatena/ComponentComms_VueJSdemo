<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="server == null">Please select a server to show the details</p>
        <div v-else>
            <p>Server #{{server.id}} Status:{{server.status}}</p>
            <button v-on:click="resetStatus">Status to Normal</button>
        </div>
    </div>
</template>

<script>
    import {eventBus} from '../../main'
    export default {
        data: function() {
            return {
                server: null
            }
        },
        methods: {
            resetStatus() {
                this.server.status = "Normal";
            }
        },
        created() {
            eventBus.$on('serverDetailsEvt', (server) => {
                this.server = server;
            });
        }
    }
</script>

<style>
</style>
