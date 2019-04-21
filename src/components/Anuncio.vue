<template>
    <div class="anuncio">
        <transition name="fade" mode="out-in">
            <span :key="index">{{ presentations[index] }}</span>
        </transition>
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
    methods: {
        showAnnounce() {
            this.index++

            if(this.index === this.presentations.length) {
                this.index = 0
            }

        }
    },
    mounted() {
        setInterval(this.showAnnounce, 3000)
    }
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

.fade-enter {
    opacity: 0;
}

.fade-enter-active {
    transition: opacity 1s ease-out;
}

.fade-leave-enter {
    transition: opacity .6s ease-out;
    opacity: 0;
}
</style>