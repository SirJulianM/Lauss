<template>
    <div class="container">
        <ul class="list-group">
            <li v-for="(item, index) of arrayOrden" :key="item.id" @click="aumentar(index)"
            class="list-group-item d-flex justify-content-between align-items-center">
                {{index}}  {{item.nombre}}
                <span class="badge badge-primary badge-pill">
                    {{item.cantidad}}
                </span>
            </li>
        </ul>
        <button class="btn btn-block btn-danger" @click="reiniciar()">Reiniciar</button>
    </div>
</template>
<script>
    import {mapState, mapMutations} from 'vuex';
    export default {
        name: 'Lista',
        computed: {
            ...mapState(['frutas']),
            arrayOrden(){
                return this.frutas.sort((a,b)=> b.cantidad - a.cantidad)
            }
        },
        methods:{
            ...mapMutations(['aumentar', 'reiniciar'])
        }
    }
</script>
<style scoped>

</style>