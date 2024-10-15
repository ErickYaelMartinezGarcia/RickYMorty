<!-- <template>
    <div :id="info.id+'idCard'" class="card h-100" :style="{'background-color':chooseColor(info.species)}">
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
</template> -->

<template>
    <div :id="info.id+'idCard'" class="rounded-3 h-100 col-lg-11 shadow py-2" :style="{'background-color':chooseColor(info.species)}">
        <div class="mx-auto col-11 text-center">
                <a type="button"@click="sendCharacterInfo(info)">
                    <img class="img-fluid mx-auto rounded-2 rounded-bottom-0" :src="info.image" alt="characters">
                </a>
            </div>
        <div class="pt-1 mx-auto my-auto px-2 ">
            <h5 class="fst-italic">
                <i class="bi bi-tag-fill"> </i>
                <span v-text="info.name"></span>
            </h5>
            <div class="row">
                <span class="col-lg-4 text-dark fw-semibold d-flex">
                        <i class="bi bi-people"></i>
                          Especie: 
                        </span>
                        <div class="col-lg-8">
                            <span class="" v-text="info.species"></span>
                        </div>
            </div>
    
                        <span class="text-dark fw-semibold">
                            <i class="bi bi-heart-pulse"></i>
                            Estatus: </span>
                            <span v-text="info.status"></span>
        </div>
    </div>
</template>
<script>

export default {
    emits:['sendCharacterInfo'],
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
                             this.info.bgColor = '#9bb5fa'
                            return '#9bb5fa';
                        case 'Alien':
                             this.info.bgColor = '#c9a0fe' 
                            return '#c9a0fe';
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
