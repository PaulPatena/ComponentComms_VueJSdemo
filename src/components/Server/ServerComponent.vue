<template>
  <li class="list-group-item"
        style="cursor: pointer"
        v-bind:class="bgLookup[server.status]"
        v-on:click="emitServerDetails">Server #{{ server.id }}</li>
</template>

<script>
    import {eventBus} from '../../main'

    export default {
        props: {
            server: {
                type: Object,
                default: null
            }
        },
        data: function() {
            return {
                bgLookup: {'Normal': 'green', 'Critical': 'red', 'Unknown': 'gray' }
            }
            
        },
        methods: {
            emitServerDetails() {
                eventBus.publishServerDetails(this.server);
            }
        }
    }
</script>

<style scoped>
    .red {
        background-color: rgba(216, 172, 172, 0.979)
    }
    .green {
        background-color: rgb(127, 194, 127)
    }
    .gray {
        background-color: rgb(187, 187, 187)
    }

</style>

