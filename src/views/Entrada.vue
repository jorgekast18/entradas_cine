<template>
    <div>
        <Anuncio/>
        <Cliente/>
        <Boletos/>
        <Firma/>
    </div>
</template>

<script>
import Cliente from '@/components/Cliente'
import Anuncio from '@/components/Anuncio'
import Boletos from '@/components/Boletos'
import Firma from '@/components/Firma'
export default {
    components: { Cliente, Anuncio, Boletos, Firma }
}
</script>

<style>
.seccion {
    font-size: 2.4rem;
    color: #202020;
    background-color: #e9e9e9;
    border-radius: 5px;
    margin: 10px;
    padding: 10px;
}

.atributo {
    margin: 10px;
}
</style>
