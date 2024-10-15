<template>
  <header>
    <div class="d-flex px-4 py-3">
      <h2 class="d-none d-sm-flex mortyBlueFont my-auto">Rick& Morty</h2>
      <div class="col-lg-5 mx-auto d-flex">
        <select class="form-select form-select-sm form-control w-25" v-model="filterSelection">
          <option value="name">Nombre</option>
          <option value="status">Estatus</option>
          <option value="species">Especie</option>
        </select>
        <!-- search BAr -->
        <div class="input-group rounded-5">
          <input type="text" class="form-control form-control-sm border-0 rounded-5 rounded-end-0" 
          placeholder="Realiza una busqueda" v-model="inputText">
          <div class="bg-white rounded-start-0 rounded-5 input-group-text border-0 text-center px-2 py-1">
            <i class="bi bi-search fs-4 text-white bg-success rounded-circle px-2"
             @click="search(filterSelection,inputText)"></i>
          </div>
         
        </div>
       
      </div>
    </div>



  </header>
</template>
<script>

export default {
  components: {},
  props: {

  },
  emit: ['sendData'],
  data() {
    return {
      filterSelection: 'name',
      inputText: ''
    }
  },
  methods: {

    search: function (filter, text) {
      if (!text) {
        return console.log('asegurate de realizar una busqueda adecuada')
      }

      this.$parent.$parent.loader = true
      //https://rickandmortyapi.com/api/character/?name=rick
      let url = `https://rickandmortyapi.com/api/character/?${filter}=${text}`
      let dato = {}
      axios.get(url, dato).then(response => {
        console.log(response)
        if (response.status == 200) {
          this.$emit("sendData", response.data)
        } else {
          this.$emit("sendData", {});
          this.$parent.$parent.loader = false;
        }
      }).catch(error => {
        this.$emit("sendData", error.response);
        this.$parent.$parent.loader = false;
        console.log('error', error);
      });
    }
  },
  mounted() {

  }
}
</script>

<style scoped>
header {
  height: 13%;
  background-color: #7cf448;
}
</style>
