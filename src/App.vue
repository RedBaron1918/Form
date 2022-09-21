<template>
  <div id="#app">
    <form class="row g-4">
      <InputStyle class="col-md-5">
        <NormalInput
          v-model="FirstName"
          type="text"
          label="First name"
          required
        />
      </InputStyle>
      <InputStyle class="col-md-5">
        <NormalInput
          v-model="LastName"
          type="text"
          label="Last Name"
          required
        />
      </InputStyle>

      <InputStyle class="col-md-10">
        <NormalInput
          v-model="Adress"
          type="text"
          label="Adress"
          required
          maxlength="35"
        />
      </InputStyle>

      <InputStyle class="col-md-3">
        <NormalInput v-model="SelectedDate" type="date" label="Select Date" />
      </InputStyle>
      <InputStyle class="col-md-3">
        <Select v-model="Gender" label="Select Gender" />
      </InputStyle>

      <InputStyle class="col-10">
        <TextArea v-model="Notes" label="Notes..." />
      </InputStyle>
    </form>
  </div>
</template>

<script>
import NormalInput from "./components/normalInput.vue";
import Select from "./components/Select.vue";
import InputStyle from "./components/InputStyle.vue";
import TextArea from "./components/TextArea.vue";
export default {
  name: "App",
  components: {
    NormalInput,
    Select,
    InputStyle,
    TextArea,
  },
  data() {
    return {
      FirstName: "",
      LastName: "",
      Adress: "",
      SelectedDate: "",
      Gender: "",
      Notes: "",
    };
  },
};
</script>
<style>
body {
  padding: 50px;
}
</style>
