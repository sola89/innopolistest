<template>
  <div class="validate-component" :class="{ active: isValid }" ref="validate">
    Validate Component
    <slot></slot>
    <div>
      <button v-if="hasChild" @click="click">Validate</button>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
  name: "ValidateComponent",
  data() {
    return {
      isValid: false,
      hasChild: false,
    };
  },
  methods: {
    validate() {
      this.isValid = true;
    },
    click() {
      this.$children.map((value) => {
        if (value.$refs.validate) {
          value.validate();
        } else {
          eventBus.$emit("parentTrigger");
        }
      });
    },
  },
  mounted() {
    if (this.$children.length) this.hasChild = true;
  },
};
</script>

<style lang="sass">
.validate-component
    padding: 15px
    margin: 10px 0
    border: 1px solid green
    background: white
    color: black
.active
    background: green
    color: #fff
</style>