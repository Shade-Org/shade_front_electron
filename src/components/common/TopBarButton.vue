<template>
  <button @click="$emit('openModalLogin')" v-if="isLogin == false">
    <p>Sign in</p>
    <img src="@/assets/user.png">
  </button>
  <button v-else @click="$emit('openModalLogOut')">
    <img src="@/assets/user.png">
    <p v-if="isLogin">{{ userName }}</p>
    <img class="adm" src="@/assets/adminbanner.png" v-if="isIn == true && isAdmin == true">
  </button>
</template>

<script>
import { mapState } from "vuex";

export default {
  name: 'TopBarButton',
  props: {
    isIn: Boolean
  },
  computed: {
    ...mapState('login', {
      userName: state => state.userName,
      isLogin: state => state.isLogin,
    }),
    ...mapState('inOrganization', {
      isAdmin: state => state.isAdmin
    }),
  },
}
</script>

<style scoped>
button{
  color:white;
  float: right;
  position: relative;
  top: calc(50% - 1.25rem);
  margin-right: 2rem;
  width: auto;
  height: 3em;
  background-color: #7b7b7b32;
  border-radius: 1.5rem;
  border: none;
  box-shadow: 0.2px 0.2px 4px 4px #0000002f;
  cursor: pointer;
}
img{
  width: 1rem;
  float: left;
  display: block;
  margin-left: 0.3rem;
  margin-right: 0.3rem;
  margin-top: 0.7rem;
}
p{
  margin-top: 0.7rem;
  margin-left: 0.3rem;
  margin-right: 0.3rem;
  float: left;
}
.adm{
  margin: 0rem;
  width: 2.2rem;
  height: 2.6rem;
  z-index: 1;
}
</style>