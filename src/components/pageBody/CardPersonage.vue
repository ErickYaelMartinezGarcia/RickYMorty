<template>
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
                             this.info.bgColor = '#fede67'
                            return '#fede67';
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
