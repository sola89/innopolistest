<template>
  <div class="home">
    <!-- 1 -->
    <validate-component>
      <some-component>
        <!-- 2 -->
        <validate-component></validate-component>
      </some-component>

      <some-component>
        <!-- 3 -->
        <validate-component>
          <!-- 4 -->
          <validate-component />
          <validate-component />
        </validate-component>
      </some-component>
      <!-- 5 -->
      <validate-component></validate-component>
    </validate-component>
  </div>
</template>

<script>
// @ is an alias to /src
import ValidateComponent from "@/components/ValidateComponent.vue";
import SomeComponent from "@/components/SomeComponent.vue";

export default {
  name: "Home",
  components: {
    ValidateComponent,
    SomeComponent,
  },
};
</script>

<style lang="sass">
.space
    margin-left: 30px
</style>
