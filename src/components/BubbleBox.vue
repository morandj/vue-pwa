<template>
  <div class="bubble-box">
    <h1>{{ msg }}</h1>
    <test-component />
    <!-- <test-button/> -->
    <!-- <test-button></test-button> -->
    <!-- <base-button/> -->
    <!-- <base-input/> -->
    <!-- <base-select/> -->
  </div>
</template>

<script>
import TestComponent from "./TestComponent.vue";
import TestButton from "./TestButton.vue";
import BaseButton from "./BaseButton.vue";
import BaseInput from "./BaseInput.vue";
import BaseSelect from "./BaseSelect.vue";
export default {
  beforeCreate() {
    console.log("before create hook");
  },
  name: "BubbleBox",
  components: {
    TestComponent,
    TestButton,
    BaseButton,
    BaseInput,
    BaseSelect
    //same as "TestButton": TestButton
  },
  props: {
    msg: String
  }
};
</script>

<style scoped>
.bubble-box {
  border: 1px solid blue;
  border-radius: 10px;
  margin: 3px;
  padding: 3px;
}

</style>
