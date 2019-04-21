<template>
    <div>
        <div class="seccion"> 
            <transition name="scale-y" mode="out-in">
                <div v-if="!paid && tickets == 0" :key="1" class="mensaje informacion">
                    Selecciona al menos un boleto.
                </div>
                <div v-else-if="!paid && tickets > 0" :key="2" class="mensaje advertencia">
                    Recuerda completar tu compra.
                </div>
                <div v-else :key="3" class="mensaje exito">
                    ¡Bienvenido!
                </div>
            </transition>
            <div class="atributo">
                <span> Asientos </span>
            </div>
            <div class="atributo">
                <transition-group name="superior">
                    <button
                        class="button"
                        @click="select(chair, index)"
                        v-for="(chair, index) in chairs" :key="chair"> {{ chair }}
                    </button>
                </transition-group>
                
            </div>
        </div>
        <div class="seccion">
            <div class="atributo">
                <span> Boletos </span>
            </div>
            <div class="atributo">
                <span class="tickets"> {{ tickets }} </span>
            </div>
            <div v-show="tickets > 0" class="atributo">
                <span> Total: ${{ total }} </span>
            </div>
            <div class="atributo">
                <transition-group name="inferior">
                    <button 
                        class="button chairsSelected" 
                        @click="removeChair(chairSelected, index)"
                        v-for="(chairSelected, index) in chairsSelected" :key="chairSelected"> {{ chairSelected }}
                    </button>
                </transition-group>
            </div>
            <div v-if="!paid && tickets > 0" class="atributo">
                <button class="button" @click="paid = true">Pagar</button>
            </div>
            <div v-if="paid" class="atributo">
                <button class="button" @click="reset()">Reiniciar</button>
            </div>
            <div class="atributo">
                <span class="commission" :class="commissionClass"> ${{ commission }} </span>
            </div>
        </div>
        <transition name="fade">
            <tiquete v-if="paid">
                <div slot="obra"> 
                    <span> El rey león</span>
                </div>
                <div slot="horario"> 
                    <span> 2019-05-21 22:10</span>
                </div>
                <div slot="asiento"> 
                    <span class="asiento" v-for="(chairSelected, index) in chairsSelected" :key="index"> {{ chairSelected }}</span>
                </div>
                <div slot="total"> 
                    <span> $ {{ total }}</span>
                </div>
            </tiquete>
        </transition>
    </div>
</template>

<script>
import Tiquete from './Ticket'

export default {
    components: { Tiquete },
    data() {
        return {
            commission: 0,
            commissionClass: 'neutro',
            paid: false,
            chairs: [
                'A1', 'A2', 'A3', 'A4', 'A5', 
                'B1', 'B2', 'B3', 'B4', 'B5', 
            ],
            chairsSelected: []
        }
    },
    computed: {
        tickets() {
            return this.chairsSelected.length
        },
        total() {
            return this.tickets * 100
        }
    },
    methods: {
        select(chair, index) {
            if(this.paid) { return }
            this.chairs.splice(index, 1)
            this.chairsSelected.push(chair)
            this.chairsSelected.sort()
        },
        removeChair(chair, index) {
            if(this.paid) { return }
            this.chairsSelected.splice(index, 1)
            this.chairs.push(chair)
            this.chairs.sort()
        },
        reset() {
            this.paid = false
            this.chairs.push(...this.chairsSelected)
            this.chairs.sort()
            this.chairsSelected = []
            this.commission = 0
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
.asiento {
    font-size: 1.8rem;
    padding: 3px;
    margin: 3px;
    border-style: solid;
    border-color: black;
    border-width: 1px;

}
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

.mensaje {
    border-radius: 5px;
    border-width: 4px;
    border-style: dashed;
    padding: 10px;
    font-size: 2.1rem;
    font-weight: bold;
}
 
.informacion{
    border-color: blue;
} 

.advertencia {
    border-color: orange;
}

.exito {
    border-color: green;
}

.chairsSelected {
    background-color: #80d80e !important;
}

.scale-y-enter {
    opacity: 0;
}

.scale-y-enter-active {
     transition: opacity .3s ease-out;
     animation: message-in .3s ease-out forwards;
}

.scale-y-leave-active {
    transition: opacity .2s ease-out;
    animation: message-out .2s ease-out forwards;
    opacity: 0;
}

@keyframes message-in {
    from {
        transform: scaleY(0)
    } to {
        transform: scaleY(1)
    }
}

@keyframes message-out {
    from {
        transform: scaleY(1)
    } to {
        transform: scaleY(0)
    }
}

.superior-enter {
    opacity: 0;
}

.superior-enter-active {
     transition: opacity .3s ease-out;
     animation: superior-in .3s ease-out forwards;
}

.superior-leave-active {
    transition: opacity .2s ease-out;
    animation: superior-out .2s ease-out forwards;
    opacity: 0;
}

@keyframes superior-in {
    from {
        transform: translateY(30px)
    } to {
        transform: translateY(0)
    }
}

@keyframes superior-out {
    from {
        transform: translateY(0)
    } to {
        transform: translateY(30px)
    }
}

.inferior-enter {
    opacity: 0;
}

.inferior-enter-active {
     transition: opacity .3s ease-out;
     animation: inferior-in .3s ease-out forwards;
}

.inferior-leave-active {
    transition: opacity .2s ease-out;
    animation: inferior-out .2s ease-out forwards;
    opacity: 0;
}

@keyframes inferior-in {
    from {
        transform: translateY(0)
    } to {
        transform: translateY(30px)
    }
}

@keyframes inferior-out {
    from {
        transform: translateY(30px)
    } to {
        transform: translateY()
    }
}
</style>
