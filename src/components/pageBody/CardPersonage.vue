<template>
<div class="col-7 mx-auto rounded-3 p-3" :style="{'background-color':chooseColor(info.species)}" style="min-height:200px;height:100%">
        <div class="rounded-2 mx-auto bg-info col-10 text-center border border-dark">
            <h3 class="d-inline text-wrap text-center" v-text="info.name"></h3>
         </div>
         <div class="mt-3 d-flex my-auto">
                    <div class="col-lg-5 col-sm-12 rounded-2 my-auto">
                            <a  @click="sendCharacterInfo(info)">
                                <img class="mx-auto img-fluid rounded-2 border" :src="info.image" alt="characters">
                            </a>
                        </div>
                        
                        <div class="col-6 mx-auto my-auto">
                            <span class="text-dark rounded-2 bg-info d-block text-center">Estatus</span>
                            <span v-text="info.status"></span>
                           <div>  
                            <span class="text-dark rounded-2 bg-info d-block text-center">Especie</span>
                                    <span v-text="info.species"></span>
                                 </div>
                        </div>
         </div>
                        

        </div>

            <!-- 
                <div class="card h-100" :style="{'background-color':chooseColor(info.species)}">
                    <div class="card-body row mx-auto">
                        <div class="col-lg-5 col-sm-12">
                            <a  @click="sendCharacterInfo(info)">
                                <img class="img-fluid mx-auto" :src="info.image" alt="characters">
                            </a>
                        
                        </div>
                        <div class="col-lg-7 col-sm-12">
                            <strong class="fs-4" v-text="info.name"></strong>
                        <div>
                            <strong class="text-dark">Estatus:</strong>
                            <span class="" style="background: greenyellow;" v-text="info.status"></span>
                        </div>
                                
                            

                            <div class="d-flex">
                                <strong class="text-dark">Especie: </strong>
                                    <span v-text="info.species"></span>
                                
                            </div>
                        </div>
                    </div>
                </div> 
            -->
</template>
<script>

export default {
    props: {
            info:{
                type:Object,
                required:true}
                },
    data() {
       return {

        }
    },
    methods: {
        sendCharacterInfo:function(information){
            this.$emit("sendCharacterInfo",information)
        },
        chooseColor:function(specie){
            switch(specie){
                        case 'Human': 
                            this.info.bgColor = '#f8f8d8'
                            return '#f8f8d8';
                        case 'Alien':
                            this.info.bgColor = '#ecdffe' 
                            return '#ecdffe';
                        case 'Animal': 
                            this.info.bgColor = '#ff746c'
                            return '#ff746c';
                        case 'Humanoid': 
                            this.info.bgColor = '#98e13b'
                            return '#98e13b';
                        case 'Cronenberg': 
                            this.info.bgColor = '#049CB3'
                            return '#049CB3';
                        default: 
                            this.info.bgColor = '#fede67'
                            return '#fede67';
            }
        }
    },
    mounted() {

    }
}
</script>

<style scoped></style>
