<template>
    <div class="anuncio">
        <span>{{ presentations[0] }}</span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            presentations: [
                'Hamilton - 20:30',
                'Frozen - 15:00',
                'Anastasia - 14:00',
                'El rey leon - 22:00'
            ],
            index: 0
        }
    },
}
</script>

<style>
.anuncio {
    margin: 10px;
    font-size: 2rem;
    border-top-color: white;
    border-top-width: 1px;
    border-top-style: solid;
    
    border-bottom-color: white;
    border-bottom-width: 1px;
    border-bottom-style: solid;
}
</style>