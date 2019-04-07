<template>
    <div class="seccion">
        <div class="atributo">
            <span>{{ names }} {{ lastNames }}</span>
        </div>
        <div class="atributo">
             <img :src="photo" :alt="names">
        </div>
        <div class="atributo">
            <a :href="biography" target="_blank">Biografía</a>
        </div>
        <div class="atributo">
            <span>Edad: {{ age }}</span>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            names: 'Isaac',
            lastNames: 'Newton',
            bornDate: new Date(1994, 9, 27),
            photo: 'https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Sir_Isaac_Newton_%281643-1727%29.jpg/220px-Sir_Isaac_Newton_%281643-1727%29.jpg',
            biography: 'https://es.wikipedia.org/wiki/Isaac_Newton'
        }
    },
    computed: {
        completeName() {
            return `${this.name} ${this.lastNames}`
        },
        age() {
            return this.calcAge(this.bornDate)
        }
    },
    methods: {
        calcAge(date) {
            let currentDate = new Date()
            let currentAge = currentDate - date
            return Math.floor(currentAge / (1000 * 60 * 60 * 24 * 365.25))
        }
    }
    
}
</script>

<style>
a {
    text-decoration: none;
    color: purple
}
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
