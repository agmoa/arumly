<template>
  <section
    class="bgImg flex flex-jcc"
    :style="{
      backgroundImage: `url(${backgroundUrl})`,
    }"
  >
    <div class="secondary p-50">
      <div class="headings">
        ACTION INSPIRES
        <br />
        COMMUNITY INSPIRES
        <br />
        CHANGE.
      </div>

      <BaseBtn class="btz -fill-1 pointer fs-p9em b mt-20 ptb-10 prl-20 mw-200">
        MEET OUR COMMUNITY
      </BaseBtn>
    </div>
  </section>
</template>

<script>
import backgroundUrl from "@/Apps/App/assets/img/arumly/banner-5-arumly.jpg";

export default {
  name: "base-hero-slot-1",

  data() {
    return {
      backgroundUrl,
    };
  },
};
</script>

<style lang="scss" scoped>
.headings {
  font-size: 1.7em;
  font-weight: bold;
}

@media (min-width: 480px) {
  .headings {
    font-size: 2.4em;
  }
}
@media (min-width: 600px) {
}
@media (min-width: 768px) {
  .headings {
    font-size: 2.7em;
  }
}
</style>
