<template>
    <div class="col-xs-12 col-sm-6">
        <p>Server id: {{ server.id }}</p>
        <p>Server status: {{ server.status }}</p>
    </div>
</template>

<script>
    import { eventBus } from '../../main.js';

    export default {
        data: function() {
            return {
                server: {
                    id: '',
                    status: 'Details are currently not updated'
                }
            }
        },
        created() {
            eventBus.$on('serverSelected', (selectedServer)=> {
                this.server = selectedServer;
            })
        }
    }
</script>

<style>

</style>
