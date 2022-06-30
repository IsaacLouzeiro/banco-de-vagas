<template>
    <div :class="estilo">
        <p>{{ titulo }}</p>
        <h2>{{ quantidade }}</h2>
    </div>
</template>

<script>
export default {
    name: 'IndicadorComum',
    props: [ 'titulo', 'quantidade' , 'bg', 'color'],
    computed: {
        estilo() {
            return `h-100 p-5 rounded-3 border ${this.bg} ${this.color}`
        }
    }
}
</script>