<template>
        <div class="row">
            <div class="col-xs-12">
                <footer>
                    <p>All Servers are managed here</p>
                    <button @click="repairServer" class="btn btn-success">Repair</button>
                    <button @click="brokeServer" class="btn btn-danger">Broke</button>
                </footer>
            </div>
        </div>
</template>

<script>
    import { eventBus } from "../../main";

    export default {
        data: function () {
            return {
                server: {
                    id: '',
                    status: 'Details are currently not updated'
                }
            }
        },
        created() {
            eventBus.$on('serverSelected', function (selectedServer) {
                this.server = selectedServer;
            });
        },
        methods: {
            repairServer() {
                eventBus.$emit('changeStatus', 'Normal');
            },
            brokeServer() {
                eventBus.$emit('changeStatus', 'Critical');
            }
        }
    }
</script>

<style>

</style>
