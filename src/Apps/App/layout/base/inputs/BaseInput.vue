<template>
  <div>
    <label v-if="label">{{ label }}</label>
    <input
      :value="value"
      @input="updateValue"
      v-bind="$attrs"
      v-on="listeners"
    />
  </div>
</template>

<script>
import { formFieldMixin } from "@/mixins/formFieldMixin";
export default {
  mixins: [formFieldMixin],
  computed: {
    listeners() {
      return {
        ...this.$attrs,
        input: this.updateValue,
      };
    },
  },
};
</script>
