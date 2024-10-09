
<template>
            <div id="login_card" class="col-lg-3 col-md-6 rounded-4 p-3" style="min-height: 350px;">
                <h2>Inicia sesion</h2>
                <div class="my-3">
                    <label for="userInput" class="form-label">Usuario</label>
                    <input id="userInput" type="text" class="form-control" 
                           placeholder="Ingresa tu usuario" aria-label="Usuario"
                           v-model="user">
                </div>
                <div class="mb-3">
                    <label for="inputPassword" class="form-label">Contraseña</label>
                    <div class="input-group">
                        <input type="password" id="inputPassword" class="form-control col-10"
                               aria-describedby="passwordHelpInline"
                               v-model="password">
                        <i class="bi bi-eye fs-4 col-2 text-center" type="button" @click="showPassword('inputPassword')"></i>
                    </div>
                    <p class="text-danger mt-2 mb-0 p-0" v-text="errorText"></p>
                    <div class="text-center">
                        <button class="btn btn-md mt-4 btn-dark mx-auto" @click="validateData(user,password)">
                            ingresar
                    </button>
                    </div>
                </div>
            </div>
    </template>
    
    <script>
    export default {
        props:{
            
        },
    
        data () {
            return {
                user:'',
                password:'',
                errorText:'',
            }
        },
        methods: {
            showPassword:function(id){
                let input = document.getElementById(id)
                    if(input && input.type == "text"){
                        input.type = "password"
                    }else{
                        input.type = "text"
                    }
            },
            validateData:function(user,pass){
                if( user == '' || pass == ''){
                    return this.errorText ='asegurate de ingresar todos los datos';
                }else{
                    if(this.validateUser(user,pass)){
                        this.$emit('autorize')
                    }
                }
            },
            validateUser:function(user,pass){
            let userPrivate = localStorage.getItem('userPrivate')
            let password = localStorage.getItem('passwordPrivate')
            if(userPrivate === user && password === pass){
                return true
            }else{
                return false
            }
        },
        },
        watch:{
    
        },
        mounted() {
            
        },
     }
    </script>
    
    
    <style scoped>

    </style>
    