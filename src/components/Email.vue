 <template>
     <div class="seccion">
         <div class="atributo">
             <input v-model="email" @keyup.enter="updateEmail" type="text">
         </div>
     </div>
 </template>

 <script>
 export default {
     props: ['emailReceived'],
     data() {
         return {
             email: ''
         }
     },
     methods: {
         updateEmail() {
             this.$emit('onChangeEmail', this.email)
         }
     },
     watch: {
       emailReceived() {
           this.email = this.emailReceived
       }  
     }
 }
 </script>
 
 <style>
 .email {
     text-align: left;
 }
 </style>
 
 