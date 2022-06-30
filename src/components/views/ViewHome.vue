<template>
    <div class="container py-4">
        <div class="row">
            <div class="col">
                <PesquisarVaga />
            </div>
        </div>

        <ListaVagas />

        <div class="row mt-5">
            <div class="col-4">
                <IndicadorComum titulo="Vagas abertas" quantidade="25" bg="bg-dark" color="text-white" />
            </div>
            <div class="col-4">
                <IndicadorComum titulo="Profissionais cadastrados" quantidade="125"  bg="bg-dark" color="text-white" />
            </div>

            <div class="col-4">
                <IndicadorComum titulo="Visitantes Online" :quantidade="usuariosOnline"  bg="bg-white" color="text-dark" />
            </div>
        </div>
    </div>
</template>

<script>
import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'
import IndicadorComum from '@/components/comuns/IndicadorComum.vue'
import ListaVagas from '@/components/comuns/ListaVagas.vue'

export default {
    name: "ViewHome",
    data() {
        return {
            usuariosOnline: 0
        }
    },

    methods: {
        getUsuariosOnline() {
            this.usuariosOnline = Math.floor(Math.random() * 101) //entre 0 e 100
        }
    },

    created() {
        setInterval(this.getUsuariosOnline, 1000) // a cada 1 segundo
    },

    components: {
        PesquisarVaga,
        IndicadorComum,
        ListaVagas
    }
}
</script>

<style lang="scss" scoped>

</style>