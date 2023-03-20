<script setup>
    const props = defineProps(['resultadoOperacao', 'condicao'])
</script>
<template>
    <div class="col-md-12 mt-5 text-center">
        <h3 v-if="props.condicao"></h3>
        <h3 v-else>O resultado é {{ props.resultadoOperacao }}</h3>
    </div>
</template>