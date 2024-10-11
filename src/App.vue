<template>
  <div>
  <LoaderPortal v-if="loader"></LoaderPortal>

  <LoginContentComponent v-if="!haveAutorize && !loader" @autorize="autorize"></LoginContentComponent>

  <ContentPage v-if="haveAutorize" v-show="!loader"/>
</div>
</template>

<script>
import LoginContentComponent from './components/login/LoginContentComponent.vue';
import LoaderPortal from './components/LoaderPortal.vue';
import ContentPage from './components/pageBody/ContentPage.vue';

export default {
  components: {
    LoginContentComponent,
    LoaderPortal,
    ContentPage,

  },
  data() {
    return {
      loader: true, 
      haveAutorize: false,
    };
  },
  methods: {
    createUser() {
      if (!localStorage.getItem('userAuthorized')) {
        localStorage.setItem('userPrivate', 'babyYoda');
        localStorage.setItem('passwordPrivate', 'HelloWord');
        localStorage.setItem('userAuthorized', 'false');
      }
      this.haveAutorize = localStorage.getItem('userAuthorized') === 'true';
    },
    autorize() {
      
      localStorage.setItem('userAuthorized', 'true');
      this.haveAutorize = true;
    },
  },
  mounted() {
    this.createUser();


    setTimeout(() => {
      this.loader = false;
    }, 2000);
  },
};
</script>

<style scoped>

</style>