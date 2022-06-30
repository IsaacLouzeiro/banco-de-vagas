<template>
    <div>
        <keep-alive>
            <component :is="conteudo" />
        </keep-alive>
    </div>
</template>

<script>
    import PublicarVaga from '@/components/views/PublicarVaga.vue'
    import ViewHome from '@/components/views/ViewHome.vue'

    export default {
        name: 'SecaoConteudo',
        props: {
            conteudo: {
                type: String,
                required: true
            }
        },
        components: {
            ViewHome,
            PublicarVaga
        }
    }
</script>

<style lang="scss" module>

    .teste1 {
        background-color: red;
    }

    .teste2 {
        background-color: yellow;
    }
</style>