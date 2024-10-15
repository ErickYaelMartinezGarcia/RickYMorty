    <style scoped>
    @media (max-width:460px) {
        .episodesSize {
            height: 100px !important;
            overflow: auto;
        }
    }
    .episodesSize{
            height: 180px;
            overflow: auto;
        }
    </style>

<template>
    <div id="modal_character_content" class="modal fade" tabindex="-1" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered modal-lg">
            <div class="modal-content" :style="'background-color:'+modalcharacter?.bgColor">
                <!-- :style="'box-shadow: 5px 5px 5px 5px'+modalInfo.bgColor"> -->
                <!-- <div class="modal-header">
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div> -->

                <div class="modal-body row">
                    <div class="col-lg-6 text-center mx-auto">
                        <img class="img-fluid mx-auto rounded-3" :src="modalcharacter?.image" alt="characters">
                    </div>
                    <div class="col-lg-6 mx-auto">
                        <div>
                            <h1 class="modal-title fs-3 fst-italic" id="exampleModalLabel">
                                <span class="" v-text="modalcharacter?.name"></span>
                            </h1>
                            <span class="">
                                <i class="bi bi-gender-ambiguous"></i> Genero:  </span>
                            <span class="badge text-dark" :class="{'text-bg-info': modalcharacter?.gender == 'Male'}"
                                :style="{ backgroundColor: modalcharacter?.gender == 'Female' ? 'rgb(255,190,205)' : '' }"
                                v-text="modalcharacter?.gender">
                            </span>
                        </div>

                        <div>
                            <span class="">
                                <i class="bi bi-geo-alt-fill text-danger"></i> Origen:  </span>
                            <span class="" v-text="modalcharacter?.origin?.name"></span>
                        </div>

                        <span class="fw-semibold">Episodio en el que aparace:</span>
                        <div class="row row-cols-md-6 row-cols-5 px-2 episodesSize">
                            <template v-for="number in episodes">
                                <div class="rounded-5 text-center mt-1 px-1" 
                                        style="font-size: .8rem;">
                                    <span class="bg-success rounded-5 d-block text-white my-auto px-2" v-text="number"></span>
                                </div>

                            </template>
                        </div>
                    </div>
                    <div>
                    </div>
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


