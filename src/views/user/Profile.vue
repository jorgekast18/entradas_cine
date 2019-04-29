<template>
    <v-layout text-xs-center align-start justify-center>
        <v-card>
            <v-card-text>
                <div class="ma-2">
                    Nombres y Apellidos
                </div>
                <img class="ma-2 pictureProfile" :src="require('@/assets/profile.png')" alt="">
                <div class="ma-2">
                    Descripción
                </div>
                <div class="ma-2">
                    <a class="link" href="">Biografía</a>
                </div>
            </v-card-text>
        </v-card>
    </v-layout>
</template>

<style>
.pictureProfile {
    width: 200px;
    height: 100%;
}

.link {
    text-decoration: none;
    font-size: 1rem;
    color: #553f75;
}
</style>
