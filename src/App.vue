<template>
  <div id="#app">
    <form class="row g-4" @submit.prevent="SubmitForm">
      <InputStyle class="col-md-5">
        <NormalInput
          v-model="FirstName"
          type="text"
          label="First name"
          :class="
            v$.FirstName.$errors.length >= 1 ? 'border border-danger' : ''
          "
        />
        <span
          style="color: red"
          v-for="error in v$.FirstName.$errors"
          :key="error.$uid"
        >
          {{ error.$message }}
        </span>
      </InputStyle>
      <InputStyle class="col-md-5">
        <NormalInput
          v-model="LastName"
          type="text"
          label="Last Name"
          :class="v$.LastName.$errors.length >= 1 ? 'border border-danger' : ''"
        />
        <span
          style="color: red"
          v-for="error in v$.LastName.$errors"
          :key="error.$uid"
        >
          {{ error.$message }}
        </span>
      </InputStyle>

      <InputStyle class="col-md-10">
        <NormalInput
          v-model="Adress"
          type="text"
          label="Adress"
          :class="v$.Adress.$errors.length >= 1 ? 'border border-danger' : ''"
        />
        <span
          style="color: red"
          v-for="error in v$.Adress.$errors"
          :key="error.$uid"
        >
          {{ error.$message }}
        </span>
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
      <InputStyle class="col-3">
        <button type="submit" class="btn btn-success">Submit</button>
      </InputStyle>
    </form>
  </div>
</template>

<script>
import NormalInput from "./components/normalInput.vue";
import Select from "./components/Select.vue";
import InputStyle from "./components/InputStyle.vue";
import TextArea from "./components/TextArea.vue";
import useVuelidate from "@vuelidate/core";
import { required, maxLength } from "@vuelidate/validators";
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
      v$: useVuelidate(),
      FirstName: "",
      LastName: "",
      Adress: "",
      SelectedDate: "",
      Gender: "",
      Notes: "",
    };
  },
  validations() {
    return {
      FirstName: { required },
      LastName: { required },
      Adress: { required, maxLengthValue: maxLength(35) },
    };
  },

  methods: {
    async SubmitForm() {
      const result = await this.v$.$validate();
      if (result) {
        console.log(result);
      } else {
      }
    },
  },
};
</script>
<style>
body {
  padding: 50px;
}
</style>
