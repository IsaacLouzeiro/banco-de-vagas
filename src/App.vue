<template>
    <div>
        <VagasFavoritas />
        <TopoPadrao @navegar="componente = $event" />
        <AlertaComum v-if="exibirAlerta" :tipo="alerta.tipo">
            <template v-slot:titulo>
                <h5>{{ alerta.titulo }}</h5>
            </template>
            <p>{{ alerta.descricao }}</p>
        </AlertaComum>
        <SecaoConteudo v-if="visibilidade == true" :conteudo="componente" />
    </div>
</template>

<script>
import SecaoConteudo from './components/layouts/SecaoConteudo.vue'
import TopoPadrao from './components/layouts/TopoPadrao.vue'
import VagasFavoritas from './components/comuns/VagasFavoritas.vue'
import AlertaComum from './components/comuns/AlertaComum.vue'

export default {
    name: 'App',
    data() {
        return {
            visibilidade: true,
            componente: 'ViewHome',
            exibirAlerta: false,
            alerta: { titulo: '', descricao: '', tipo: '' }
        }
    },
    components: {
        SecaoConteudo,
        TopoPadrao,
        VagasFavoritas,
        AlertaComum
    },

    mounted() {
        this.emitter.on('alerta', (a) => {
            this.alerta = a
            console.log(this.alerta)
            this.exibirAlerta = true
            setTimeout(() => {
                this.exibirAlerta = false
            }, 4000);
        })
    }
}
</script>

<style lang="scss" scoped>

</style>
