<script setup>
    const props = defineProps(['numeroA', 'numeroB', 'pegaNumeroA', 'pegaNumeroB', 'mudaOperacao'])
</script>
<template>
    <form class="text-center mt-5">
        <div class="row d-flex justify-content-center">
            <div class="col-md-2">
                <input :value="props.numeroA" @keyup="props.pegaNumeroA" type="text"
                    placeholder="Insira um número" class="form-control">
            </div>
            <div class="col-md-1">
                <select @change="props.mudaOperacao" class="form-select">
                    <option value="adicao">+</option>
                    <option value="subtracao">-</option>
                    <option value="multiplicacao">x</option>
                    <option value="divisao">/</option>
                </select>
            </div>
            <div class="col-md-2">
                <input :value="props.numeroB" @keyup="props.pegaNumeroB" type="text"
                    placeholder="Insira um número" class="form-control">
            </div>
        </div>
    </form>
</template>