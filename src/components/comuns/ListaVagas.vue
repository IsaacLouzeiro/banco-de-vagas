<template>
    <slot :vagas="vagas">
        <div class="row mt-5" v-for="(item, index) in vagas" :key="index">
            <div class="col">
                <VagaComum v-bind="item" />
            </div>
        </div>
    </slot>
</template>

<script>
import VagaComum from '@/components/comuns/VagaComum.vue'

export default {
    name: 'ListaVagas',
    data() {
        return {
            vagas: []
        }
    },
    components: {     
        VagaComum
    },
    activated() {
        this.vagas = JSON.parse(localStorage.getItem('vagas'))
    },
    mounted() {
        this.emitter.on('filtrarVagas', vaga => {
            const vagas = JSON.parse(localStorage.getItem('vagas'))
            this.vagas =vagas.filter(reg => reg.titulo.toLowerCase().includes(vaga.titulo.toLowerCase())) // true ou false: O metodo filter cria um novo array com todos os elementos que passaram no teste implementado na funcao
        })
    },
}
</script>