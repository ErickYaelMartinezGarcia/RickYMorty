<style scoped>
@import '/fonts/fonts.css';

#fontFamily {
  font-family: 'prueba';
  font-size: 6rem;
  color: #00aeff;
  -webkit-text-stroke: 2px rgb(0, 192, 0);
}
@media (max-width: 460px) {
  #fontFamily {
    font-size: 4rem;
    font-family: 'prueba';
   color: #00aeff;
    -webkit-text-stroke: 2px rgb(0, 192, 0);
  }
}

  #loader{
    min-height: 100vh;
    background-image: url('/images/darkStars.jpg');
    /* background-color: rgba(4, 23, 75, 0.651); */
  }
  </style>
  
    
    <template>
        <div id="loader" class="d-flex justify-content-center align-items-center">
            <div class="col-lg-5 col-md-6 col-8" style=" min-height: 300px;">
              <h1 id="fontFamily" class="text-center">Cargand0...</h1>
              <img class="img-fluid mx-auto d-block " 
                src="/images/portal.gif" alt="gif-Portal">
            </div>
        </div>
    </template>

  
 