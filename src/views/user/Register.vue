<template>
<v-layout justify-center align-center>
    <v-flex xs12 sm8 md6 lg5 xl4>
        <v-slide-y-transition mode="out-in">
            <v-card v-if="view === 1" :key="1" class="elevation-6">
                <v-toolbar color="primary" dark card>
                    <v-toolbar-title>
                        Regístrate
                    </v-toolbar-title>
                </v-toolbar>
                <v-card-text>
                    <v-text-field label="email"></v-text-field>
                    <v-text-field label="password" type="password"></v-text-field>
                </v-card-text>
                <v-card-text>
                    <v-layout justify-end>
                        <v-btn @click="view++" color="secondary">Siguiente</v-btn>
                    </v-layout>
                </v-card-text>
            </v-card>
            <v-card v-if="view === 2" :key="2" class="elevation-6">
                <v-toolbar color="primary" dark card>
                    <v-toolbar-title>
                        Ingresa tus nombres y apellidos
                    </v-toolbar-title>
                </v-toolbar>
                <v-card-text>
                    <v-text-field label="nombre"></v-text-field>
                    <v-text-field label="apellido"></v-text-field>
                </v-card-text>
                <v-card-text>
                    <v-layout justify-end>
                        <v-btn @click="view++" color="secondary">Siguiente</v-btn>
                    </v-layout>
                </v-card-text>
            </v-card>
            <v-card v-if="view === 3" :key="3" class="elevation-6">
                <v-toolbar color="primary" dark card>
                    <v-toolbar-title>
                        ¿Cuándo cumples años?
                    </v-toolbar-title>
                </v-toolbar>
                <v-card-text>
                    <v-layout justify-center>
                        <v-date-picker v-model="bornDate" reactive locale="es-co" class="elevation-6"></v-date-picker>
                    </v-layout>
                </v-card-text>
                <v-card-text>
                    <v-layout justify-end>
                        <v-btn color="secondary">Terminar</v-btn>
                    </v-layout>
                </v-card-text>
            </v-card>
        </v-slide-y-transition>
    </v-flex>
</v-layout>
    
</template>

<script>
export default {
    data() {
        return {
            view: 1,
            bornDate: null
        }
    }
}
</script>
