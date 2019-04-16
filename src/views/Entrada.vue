<template>
    <div>
        <Anuncio/>
        <Cliente :email="email" @onChangeEmail="updateEmail"/>
        <Email :emailReceived="email" @onChangeEmail="updateEmail"/>
        <Boletos/>
        <Firma/>
    </div>
</template>

<script>
import Cliente from '@/components/Cliente'
import Anuncio from '@/components/Anuncio'
import Boletos from '@/components/Boletos'
import Firma from '@/components/Firma'
import Email from '@/components/Email'
export default {
    components: { Cliente, Anuncio, Boletos, Firma, Email },
    data() {
        return {
            email: ''
        }
    },
    methods: {
        updateEmail(email  ) {
            this.email = email
        }
    }
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
