<template>
  <main class="base-view pb-90">
    <BaseBreadCrumb1
      title1="HOME"
      route1="home"
      title2="SHOP"
      route2="shop-all-products"
      :title3="title3Sub"
      :route3="route3Sub"
    />

    <section>
      <ShopNavigation class="header-nav" />

      <router-view class="shop-views auto"></router-view>
    </section>
  </main>
</template>

<script>
import ShopNavigation from "@/Apps/Shop/layout/ShopNavigation.vue";

export default {
  name: "shop-page",
  components: {
    ShopNavigation,
  },
  data() {
    return {
      title3Sub: "",
      route3Sub: "",
    };
  },
  methods: {
    subRoute() {
      const route = this.$route.name;
      if (route === "shop-all-products") {
        this.title3Sub = "ALL";
        this.route3Sub = "shop-all-products";
      } else if (route === "shop-notebooks") {
        this.title3Sub = "NOTEBOOKS";
        this.route3Sub = "shop-notebooks";
      } else if (route === "shop-paper") {
        this.title3Sub = "PAPER";
        this.route3Sub = "shop-paper";
      } else if (route === "shop-writing-tools") {
        this.title3Sub = "WRITING TOOLS";
        this.route3Sub = "shop-writing-tools";
      } else if (route === "shop-paint") {
        this.title3Sub = "PAINT";
        this.route3Sub = "shop-paint";
      }
    },
  },
  updated() {
    this.subRoute();
  },
};
</script>

<style lang="scss" scoped>
.shop-views {
  max-width: 999px;
}
section {
  padding: 15px;
}

@media (min-width: 600px) {
  section {
    padding: 45px;
  }
}
</style>
