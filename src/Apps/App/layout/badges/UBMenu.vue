<template>
  <div class="dropdown-menu ptb-10 uppercase" @click="$emit('showUBMenu')">
    <!-- <router-link class="route pointer flex flex-aic" :to="{ name: '' }">
      <div class="fs-1em b">ACCOUNT</div>
    </router-link> -->

    <router-link class="route pointer flex flex-aic" :to="{ name: 'cart' }">
      <div class="fs-1em b">
        CHECKOUT <span>( {{ items.length }} )</span>
      </div>
    </router-link>

    <div
      v-if="isAuthenticated"
      class="logout pointer flex flex-aic"
      @click="onLogout"
    >
      <div class="fs-1em b">LOGOUT</div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  name: "UB-Menu",
  computed: {
    ...mapState({
      items: (state) => state.CheckoutModule.cartItems,
    }),
  },
  methods: {
    fetch() {
      this.$store.dispatch("fetchCartItems");
    },

    onLogout() {
      this.$store.dispatch("logout");
    },
  },

  created() {
    this.fetch();
  },
};
</script>

<style lang="scss" scoped>
.dropdown-menu {
  position: absolute;
  top: 55px;
  right: 2px;
  font-size: 0.9em;
  font-weight: bold;
  background-color: #ffffff;
  width: 170px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
  border-bottom-left-radius: 2px;
  border-bottom-right-radius: 2px;
  border: 2px solid #000000;
}

.route,
.logout {
  padding: 12px 0px;
  padding-left: 35px;
  font-size: 1.1em;

  img {
    width: 20px;
  }
}
.route:hover {
  color: #000000;
  background-color: #f9f0f4;
}
</style>
