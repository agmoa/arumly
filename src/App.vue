<template>
  <div class="site_container">
    <!--/.HEADERS-->
    <router-view class="Header-Main" name="Header-Main"></router-view>
    <router-view class="Navigation-Main" name="Navigation-Main"></router-view>

    <!--/.BANNERS-->
    <router-view
      class="Banner-Promo mt-55 w-100p"
      name="Banner-Promo"
    ></router-view>

    <!--/.SIDENAVS-->
    <router-view class="SideNav-Bar mt-55" name="SideNav-Bar"></router-view>

    <!--/.VIEWS-->
    <div class="site_content">
      <router-view></router-view>
    </div>

    <!--/.MODALS-->
    <!-- <Modal v-if="modalModal" /> -->

    <!--/.NOTIFICATIONS-->
    <!-- <NotificationContainer class="notification" /> -->

    <!--/.FOOTERS-->
    <router-view class="Footer-Main" name="Footer-Main"></router-view>
  </div>
</template>

<script>
import axios from "axios";

import { mapState } from "vuex";

export default {
  created() {
    /* ====== Get Token START ====== */
    const tokenString = localStorage.getItem("idToken");
    // if (tokenString) {
    //   this.$store.commit("SET_AUTH_TOKEN", tokenString);
    // }

    if (tokenString) {
      this.$store.dispatch("fetchLoggedInUser");
    }
    /* ====== Get Token END ====== */

    /* ====== Refresh The Token START ====== */
    // const refreshToken = localStorage.getItem("refresh_token");
    // const now = new Date().toString();
    // const exp = localStorage.getItem("exp");

    // if (refreshToken && now >= exp) {
    //   localStorage.removeItem("idToken");
    //   this.$store.dispatch("refreshTheToken");
    // }
    /* ====== Refresh The Token END ====== */

    axios.interceptors.response.use(
      // insures that no one can trick the auto login method
      (response) => response,
      (error) => {
        if (error.response.status === 401) {
          this.$store.dispatch("logout");
        }
        return Promise.reject(error);
      }
    );
  },

  components: {
    // modalModal,
    // NotificationContainer,
  },

  computed: {
    ...mapState({
      modalModal: (state) => state.Module.modalModalStatus,
    }),
  },
};
</script>

<style lang="scss">
@import "@/Apps/App/assets/css/style.scss";

body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  margin: 0;
  line-height: 1.5;
  font-size: 14px;
  font-weight: normal;
  color: #000000;
  background-color: #ffffff;
  // background: radial-gradient(#3b4757, #2b323b);
}

h1,
h2,
h3,
h4,
h5 {
  font-weight: bold;
  line-height: 1;
  margin: 0;
  text-transform: none;
  margin-left: 0;
  margin-right: 0;
  font-weight: 450;
}

h1 {
  font-size: 2em;
}
h2 {
  font-size: 1.5em;
}
h3 {
  font-size: 1.17em;
}
h4 {
  font-size: 1em;
}
h5 {
  font-size: 1em;
}
h6 {
  font-size: 0.67em;
}

/* ======= BASE COLORS ======= */
.primary {
  color: #000000 !important;
}
.secondary {
  color: #ffffff !important;
}
.tertiary {
  color: #888888 !important;
}
.quaternary {
  color: #00ceff !important;
}
.quinary {
  color: #bcd2ed !important;
}
.senary {
  color: #232733 !important;
}

.primary-bg {
  background-color: #ffffff !important;
}
.secondary-bg {
  background-color: #bdc0c9 !important;
}
.tertiary-bg {
  background-color: #000000 !important;
}
.quaternary-bg {
  background-color: #00ceff !important;
}
.quinary-bg {
  background-color: #bcd2ed !important;
}
.senary-bg {
  background-color: #232733 !important;
}

/* ======= LINKS ======= */
a:link {
  text-decoration: none;
  color: #000000;
}

a:visited {
  text-decoration: none;
  color: #000000;
}

a:hover {
  text-decoration: none;
  color: #000000;
}

a:active {
  text-decoration: none;
  color: #000000;
}
.disabled-link {
  color: #57595e !important;
  cursor: not-allowed !important;
  img {
    opacity: 0.5;
  }
}

/* ====== VIEWS ====== */
.base-view,
.side-view,
.gen-view {
  margin-top: 55px;
  // padding: 20px;
}

@media (min-width: 768px) {
  .side-view {
    margin-left: 65px;
  }
}

@media (min-width: 1200px) {
  .side-view {
    margin-left: 200px;
  }
}
</style>
