<template>
    <div class="seccion">
        <div class="atributo">
            <span class="boletos"> {{ boletos }} </span>
        </div>
        <div class="atributo">
            <button class="button" @click="updateQuantity(- 1)">-</button>
            <button class="button" @click="updateQuantity(1)">+</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            boletos: 0
        }
    },
    methods: {
        updateQuantity(quantity) {
            this.boletos += quantity

            if(this.boletos > 10) {
                this.boletos = 10
            } else if (this.boletos < 0) {
                this.boletos = 0
            }
        }
    }
}
</script>

<style>
.boletos {
    font-size: 4rem;
    font-weight: bold;
}
</style>
