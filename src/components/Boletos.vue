<template>
    <div class="seccion">
        <div class="atributo">
            <span> Boletos </span>
        </div>
        <div class="atributo">
            <span class="tickets"> {{ tickets }} </span>
        </div>
        <div class="atributo">
            <button class="button" @click="updateQuantity(- 1)">-</button>
            <button class="button" @click="updateQuantity(1)">+</button>
        </div>
        <div class="atributo">
            <span class="commission" :class="commissionClass"> ${{ commission }} </span>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tickets: 0,
            commission: 0,
            commissionClass: 'neutro'
        }
    },
    methods: {
        updateQuantity(quantity) {
            this.tickets += quantity

            if(this.tickets > 10) {
                this.tickets = 10
            } else if (this.tickets < 0) {
                this.tickets = 0
            }
        }
    },
    watch: {
        tickets(newValue, oldValue) {
            if(newValue > oldValue) {
                this.commission += 10
            } else {
                this.commission -= 15
            }

            if(this.commission < 0) {
                this.commission = 0
            }
        },
        commission(newValue, oldValue) {
            if(this.commission === 0){
                this.commissionClass = 'neutro'
            } else if(newValue > oldValue){
                this.commissionClass = 'increment'
            } else {
                this.commissionClass = 'decrement'
            }
        }
    }
}
</script>

<style>
.tickets {
    font-size: 4rem;
    font-weight: bold;
}

.commission {
    font-size: 3.2rem;
}

.neutro {
    color: black;
}

.increment {
    color: green;
}

.decrement {
    color: red;
}
</style>
