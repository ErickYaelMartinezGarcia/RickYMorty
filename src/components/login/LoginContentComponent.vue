
<template>
<header class="d-flex justify-content-center align-items-center">
        <LoginCard @autorize="this.$emit('autorize')"></LoginCard>
</header>
</template>

<script>
import LoginCard from './LoginCard.vue';

export default {
    props:{
       
    },
    components: {
    LoginCard
  },
    data () {
        return {

        }
    },
    methods: {
    },
    mounted(){
       
    },
 }
</script>


<style scoped>
 header {
    position: relative;
    min-height: 100vh;
    background-image: url(/public/images/rickBg.jpg);
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

#login_card{
    background-color: rgba(202, 210, 216, 0.8);
}
</style>
