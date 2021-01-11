<template>
  <div class="some-component" ref="some">
    Some Component
    <slot></slot>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
  name: "SomeComponent",
  data() {
    return {
      emProp: false,
    };
  },
  mounted() {
    eventBus.$on("parentTrigger", () => {
      this.$children.map((value) => {
        if (value.$refs.validate) value.validate();
      });
    });
  },
};
</script>

<style lang="sass">
.some-component
    margin: 10px 0
    padding: 15px
    border: 1px solid red
</style>