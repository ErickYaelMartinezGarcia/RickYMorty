<template>
  <div>

    <ModalCharacter :modalInfo="modalInfo"></ModalCharacter>
    <!-- header -->
    <HeaderContent @send-data="catchData"></HeaderContent>

    <!-- body -->
    <div class="row mx-auto my-auto" v-if="error == false">
      <template v-if="Object.values(data).length > 0">
        <div v-for="character in data" class="col-lg-4 col-6 mx-auto my-3 ">
          <cardPersonage :info="character" @send-character-info="getCharacterInfo"></cardPersonage>
        </div>
      </template>
    </div>
    <Error404 v-if="error"></Error404>

    <!-- paginatpr -->

    <div class="d-flex justify-content-end mt-3 col-lg-11 ">
      <nav aria-label="Page navigation example">
        <ul class="pagination">
          <li class="page-item">
            <a class="page-link"@click="(pages[0]>=2 && pages[1]!=2)?nextPrevPage('prev'):''" aria-label="Previous">
              <span aria-hidden="true">&laquo;</span>
            </a>
          </li>
          <template v-for="page in pages">
            <li class="page-item" @click="goToPage(page)">
              <a class="page-link" v-text="page"></a>
            </li>
          </template>
                
          <li class="page-item">
            <a class="page-link" @click="nextPrevPage('next')" aria-label="Next">
              <span aria-hidden="true">&raquo;</span>
            </a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>
<script>

import cardPersonage from './CardPersonage.vue';
import HeaderContent from './header/HeaderContent.vue';
import ModalCharacter from './ModalCharacter.vue';
import Error404 from "../Error404.vue"


export default {
  components: {
    cardPersonage,
    HeaderContent,
    ModalCharacter,
    Error404
  },
  props: {

  },
  data() {
    return {
      pages:[1,2,3],
      data: {},
      infoPagination:{},
      modalInfo: {},
      error:false,
    }
  },
  methods: {
    goToPage:function(page){
      this.$parent.loader = true
      this.getData(`https://rickandmortyapi.com/api/character?page=${page}`)
    },
    nextPrevPage:function(direcction){
      this.$parent.loader = true
      if(direcction == 'next'){
          this.pages.shift()
          this.pages.push(this.pages[1]+1)
          this.getData(this.infoPagination.next)
      }else{
        this.pages.pop()
          this.pages.unshift(this.pages[0]-1)
          this.getData(this.infoPagination.prev)
      }
    },
    getCharacterInfo: function (info) {
      this.modalInfo = info
      this.openModal()
    },
    openModal: function () {
      const myModal = new bootstrap.Modal(document.getElementById('modal_character_content'))
      myModal.show()
    },
    catchData: function (data) {
      
      if(Object.values(data).length<1){
        this.$parent.loader = false 
        this.error = true
        return
      }
      this.data = data.results
      this.infoPagination = data.info
      this.$parent.loader = false
    },
    getData: function (url, dato) {
      axios.get(url, dato).then(response => {
        if (response.status == 200) {
         this.infoPagination = response.data.info
          this.data = response.data.results
          this.error = false
          this.$parent.loader = false
        }
      }).catch(error => {
        this.error = true
        this.$parent.loader = false
        console.log(error)
      })
    }
  },
  mounted() {
    this.getData('https://rickandmortyapi.com/api/character', {})
  }
}
</script>

<style scoped></style>