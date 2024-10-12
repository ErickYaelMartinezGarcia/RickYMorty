<template>
    <div id="modal_character_content" class="modal fade" tabindex="-1" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content" :style="'background-color:'+modalcharacter?.bgColor">
                <!-- :style="'box-shadow: 5px 5px 5px 5px'+modalInfo.bgColor"> -->
                <div class="modal-header">
                      <!-- <h1 class="modal-title fs-3 mortyBlueFont" id="exampleModalLabel" v-text="modalcharacter?.name"></h1> -->
                    <h1 class="modal-title fs-3" id="exampleModalLabel">Detalles de: 
                        <span class="" v-text="modalcharacter?.name"></span>
                    </h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body row">
                    <div class="col-6 mx-auto">
                        <img class="img-fluid mx-auto rounded-3" :src="modalcharacter?.image" alt="characters">
                    </div>
                    <div class="col-lg-6">
                        <div class="">
                            
                            <span class="fw-semibold">Genero<i class="bi bi-gender-ambiguous"></i> :</span>
                            <span class="badge text-dark" :class="{'text-bg-info': modalcharacter?.gender == 'Male'}"
                                :style="{ backgroundColor: modalcharacter?.gender == 'Female' ? 'rgb(255,190,205)' : '' }"
                                v-text="modalcharacter?.gender">
                            </span>
                        </div>
                        <div class="">
                            <span class="fw-semibold">Origen<i class="bi bi-geo-alt-fill text-danger"></i>:</span>
                            <span class="" v-text="modalcharacter?.origin?.name"></span>
                        </div>

                        <span class="fw-semibold">Episodio en el que aparace:</span>
                        <div class="row row-cols-6">
                            <template v-for="number in episodes">
                                <div class="col bg-success rounded-5 text-center col m-1">
                                    <span class="text-white" v-text="number"></span>
                                </div>
                                
                            </template>
                        </div>
                    </div>


                    <div>
                        <!-- <span v-if="modalcharacter?.episode" v-text="getEpisodes(modalcharacter?.episode)"></span> -->
                    </div>
                </div>
                <div class="modal-footer">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        modalcharacter: {
            type: Object
        }
    },

    data() {
        return {
            episodes: [],
        }
    },
    methods: {
        getEpisodes: function (arrEpisodes) {
            let copyArr = [...arrEpisodes]
            let list = copyArr.map(Url => {
                return Url.replace('https://rickandmortyapi.com/api/episode/', ' ')
            }) 
            this.episodes = list
        },
    
    },
    beforeUpdate() {
            this.getEpisodes(this.modalcharacter.episode)
    }
}
</script>


<style scoped></style>
