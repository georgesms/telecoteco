<template>
  <v-app light>
    <v-navigation-drawer v-model="drawer" app overflow width="320" style="background-color:#FFF8E1;">
      <Menu />
    </v-navigation-drawer>

    <v-app-bar app elevate-on-scroll>
      <v-row>
        <v-col md="auto" >
          <v-app-bar-nav-icon @click.stop="drawer= !drawer"></v-app-bar-nav-icon>
        </v-col>
        <Player v-if="pageType == 'EXERCISE'"/>
        <!--<v-col align="right">
          <inline-svg
            style="margin-left:10px; cursor:pointer;"
            width="100"
            height="50"
            :src="require(`../public/assets/icons/logo_big8.svg`)"
            @click="goToHello()"
          />
        </v-col>-->
      </v-row>
      
    </v-app-bar>

    <v-main>
      <v-container class="fill-height" fluid>
        <v-row align="center">
          <v-col>
            <Hello v-if="pageType == 'HELLO'"/>
            <Exercise v-if="pageType == 'EXERCISE'"/>
            <References v-if="pageType == 'REFERENCES'"/>
            <About v-if="pageType == 'ABOUT'"/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>

    <!--<v-footer inset app>
      
    </v-footer>-->
  </v-app>
</template>

<script>
import { mapMutations, mapGetters } from "vuex";
import Hello from "./components/Hello.vue";
import Player from "./components/Player.vue";
import Menu from "./components/Menu.vue";
import Exercise from "./components/Exercise.vue";
import References from "./components/References.vue";
import About from "./components/About.vue";
export default {
  methods: {
    ...mapMutations(['goToHello'])
  },
  computed: {
    ...mapGetters(["pageType"]),
    drawer: {
      // getter
      get: function () {
        return this.$store.state.appDrawer
      },
      // setter
      set: function (newValue) {
        this.$store.commit("setAppDrawer", newValue);
      }
    }
  },
  components: {
    Hello,
    Exercise,
    Player,
    Menu,
    References,
    About
  },
  // data: () => ({
  //   drawer: null
  // })
};
</script> 

<style scoped>
/* .v-application {
  background-color: #FFFFFF;
} */
/* .theme--light {
  background-color: #c01515 !important;
} */
.v-main {
  background-color:#FFF8E1;
}
.v-app-bar{
  background-color: #FFECB3 !important;
}
.v-application{
  font-family: IBM Plex Sans;
}
</style>