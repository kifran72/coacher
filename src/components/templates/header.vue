<template>
  <q-header elevated>
    <q-toolbar class="bg-black">
      <!-- <q-btn flat @click="drawer = !drawer" round dense icon="menu" /> -->
      <q-toolbar-title to="/"> CoacheR</q-toolbar-title>
      <Signup v-if="!user" />
      <Login v-if="!user" />
      <Profil v-if="user" :user="user" clickable />
      <Logout v-if="user" :user="user" />
      <!-- <q-separator inset spaced /> -->
      <q-btn
        v-if="dark.isActive"
        icon="brightness_7"
        stretch
        flat
        @click="dark.set(false)"
      />
      <q-btn
        v-if="!dark.isActive"
        icon="mode_night"
        stretch
        flat
        @click="dark.set(true)"
      />
    </q-toolbar>
  </q-header>
</template>

<script>
import { useQuasar } from "quasar";
import { ref } from "vue";
import Login from "../dialog/login.vue";
import Signup from "../dialog/signup.vue";
import Logout from "../dialog/logout.vue";
import Profil from "../dialog/profil.vue";

export default {
  name: "Header",
  props: ["user"],
  setup() {
    const $q = useQuasar();
    return {
      leftDrawerOpen: ref(false),
      dark: $q.dark,
      drawer: ref(false),
      miniState: ref(true),
      modifyModal: ref(false),
      isPwd: ref(true),
    };
  },
  methods: {
    openLogin() {
      this.modifyModal = true;
    },
    login() {
      console.log("logged");
      console.log(localStorage);
    },
    test() {
      console.log(localStorage);
    },
  },
  components: {
    Login,
    Signup,
    Logout,
    Profil,
  },
};
</script>
