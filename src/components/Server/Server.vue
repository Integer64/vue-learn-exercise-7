<template>
    <li class="list-group-item" @click="selectServer()">
        Server #{{ config.id }}
    </li>
</template>

<script>
    import { eventBus } from '../../main.js';

    export default {
        props: ['config'],
        created() {
            eventBus.$on('changeStatus', (status)=> {
                this.config.status = status;
            })
        },
        methods: {
            selectServer() {
                eventBus.$emit('serverSelected', this.config);
            }
        }
    }
</script>

<style scoped>

</style>