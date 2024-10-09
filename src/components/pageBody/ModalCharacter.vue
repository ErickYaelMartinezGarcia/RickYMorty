<template>
    <div id="modal_character_content" class="modal fade" tabindex="-1" aria-labelledby="exampleModalLabel"
        aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered" >
            <div class="modal-content" :style="'background-color:'+modalInfo?.bgColor">
                <!-- :style="'box-shadow: 5px 5px 5px 5px'+modalInfo.bgColor"> -->
                <div class="modal-header">
                    <h1 class="modal-title fs-3 mortyBlueFont" id="exampleModalLabel" v-text="modalInfo.name"></h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body row">
                    <div class="col-lg-4 col-6 mx-auto">
                        <img class="img-fluid mx-auto rounded-circle" :src="modalInfo.image" alt="characters">
                    </div>
                    <div class="col-lg-8">
                        <div class="">
                            <span>Genero<i class="bi bi-gender-ambiguous"></i> :</span>
                            <span class="badge text-dark" :class="{'text-bg-info': modalInfo.gender == 'Male'}"
                                :style="{ backgroundColor: modalInfo.gender == 'Female' ? 'rgb(255,190,205)' : '' }"
                                v-text="modalInfo.gender">
                            </span>
                        </div>
                        <div class="">
                            <span>Origen<i class="bi bi-geo-alt-fill text-danger"></i>:</span>
                            <span class="badge text-dark" v-text="modalInfo.origin?.name"></span>
                        </div>

                        <span>Episodio en el que aparace:</span>
                        <div class="row-cols-6 mx-auto">
                            <template v-for="number in episodes">
                                <span class="badge text-bg-success mx-1" v-text="number">

                                </span>
                            </template>
                        </div>
                    </div>


                    <div>
                        <span v-if="modalInfo?.episode" v-text="getEpisodes(modalInfo?.episode)"></span>
                    </div>
                </div>
                <div class="modal-footer">
                    <!-- <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    <button type="button" class="btn btn-primary">Save changes</button> -->
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        modalInfo: {
            type: Object,
            required: true
        }
    },

    data() {
        return {
            episodes: [],
        }
    },
    methods: {
        getEpisodes: function (arrEpisodes) {
            let list = arrEpisodes.map(Url => {
                return Url.replace('https://rickandmortyapi.com/api/episode/', ' ')
            })
            this.episodes = list
        },
    },
    
}
</script>


<style scoped></style>
