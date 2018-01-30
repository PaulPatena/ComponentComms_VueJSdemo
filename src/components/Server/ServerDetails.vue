<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="server == null">Please select a server to show the details</p>
        <div v-else>
            <p>Server #{{server.id}} Status:{{server.status}}</p>
            <button v-on:click="resetStatus('Normal')">Set to Normal</button>
            <button v-on:click="resetStatus('Critical')">Set to Critical</button>
            <button v-on:click="resetStatus('Unknown')">Set to Unknown</button>
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
            resetStatus(newStatus) {
                this.server.status = newStatus;
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
