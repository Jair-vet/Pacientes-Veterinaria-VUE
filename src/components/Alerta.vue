<script setup>
    import { computed } from 'vue';

    const props = defineProps({
        alerta: {
            type: Object,
            required: true
        }
    })

    const isError = computed(() => {
        return props.alerta.tipo === 'error'
    })
</script>


<template>
    <div 
        :class="[isError ? 'bg-red-200 text-red-900' : 'bg-green-200 text-green-900']"
        class="p-2 text-center rounded-md mb-3"
    >
        <p class="uppercase">{{ alerta.mensaje }}</p>
    </div>
</template>

