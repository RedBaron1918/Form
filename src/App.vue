<template>
  <div id="#app">
    <form class="row g-4">
      <NormalInput
        v-model="FirstName"
        type="text"
        label="First name"
        required
      />
      <NormalInput v-model="LastName" type="text" label="Last Name" required />
      <BiggerInput
        v-model="Adress"
        type="text"
        label="Adress"
        required
        maxlength="35"
      />
      <SmallInput v-model="SelectedDate" type="date" label="Select Date" />
      <Select v-model="Gender" label="Select Gender" />
      <InputStyle class="col-5">
        <Test v-model="FirstName" type="text" label="First name" required />
      </InputStyle>
    </form>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import NormalInput from "./components/normalInput.vue";
import BiggerInput from "./components/biggerInput.vue";
import SmallInput from "./components/SmallInput.vue";
import Select from "./components/Select.vue";
import Test from "./components/Test.vue";
import InputStyle from "./components/InputStyle.vue";
export default {
  name: "App",
  components: {
    Form,
    NormalInput,
    BiggerInput,
    SmallInput,
    Select,
    Test,
    InputStyle,
    Test,
  },
  data() {
    return {
      FirstName: "",
      LastName: "",
      Adress: "",
      SelectedDate: "",
      Gender: "",
    };
  },
};
</script>
<style>
body {
  padding: 50px;
}
</style>
