<template>
  <div id="#app">
    <form class="row g-4" @submit.prevent="SubmitForm">
      <InputStyle class="col-md-5">
        <NormalInput
          v-model="FormValues.FirstName"
          type="text"
          label="First name"
          :class="
            v$.FormValues.FirstName.$errors.length >= 1
              ? 'border border-danger'
              : ''
          "
        />
        <span
          style="color: red"
          v-for="error in v$.FormValues.FirstName.$errors"
          :key="error.$uid"
        >
          {{ error.$message }}
        </span>
      </InputStyle>
      <InputStyle class="col-md-5">
        <NormalInput
          v-model="FormValues.LastName"
          type="text"
          label="Last Name"
          :class="
            v$.FormValues.LastName.$errors.length >= 1
              ? 'border border-danger'
              : ''
          "
        />
        <span
          style="color: red"
          v-for="error in v$.FormValues.LastName.$errors"
          :key="error.$uid"
        >
          {{ error.$message }}
        </span>
      </InputStyle>

      <InputStyle class="col-md-10">
        <NormalInput
          v-model="FormValues.Adress"
          type="text"
          label="Adress"
          :class="
            v$.FormValues.Adress.$errors.length >= 1
              ? 'border border-danger'
              : ''
          "
        />
        <span
          style="color: red"
          v-for="error in v$.FormValues.Adress.$errors"
          :key="error.$uid"
        >
          {{ error.$message }}
        </span>
      </InputStyle>

      <InputStyle class="col-md-3">
        <NormalInput
          v-model="FormValues.SelectedDate"
          type="date"
          label="Select Date"
        />
      </InputStyle>
      <InputStyle class="col-md-3">
        <Select v-model="FormValues.Gender" label="Select Gender" />
      </InputStyle>

      <InputStyle class="col-10">
        <TextArea v-model="FormValues.Notes" label="Notes..." />
      </InputStyle>
      <InputStyle class="col-3">
        <button type="submit" class="btn btn-success">Submit</button>
      </InputStyle>
    </form>

    <Table :FormResult="FormResult" />
  </div>
</template>

<script>
import NormalInput from "./components/normalInput.vue";
import Select from "./components/Select.vue";
import InputStyle from "./components/InputStyle.vue";
import TextArea from "./components/TextArea.vue";
import Table from "./components/Table.vue";
import useVuelidate from "@vuelidate/core";
import { required, maxLength } from "@vuelidate/validators";
export default {
  name: "App",
  setup() {
    return { v$: useVuelidate() };
  },
  components: {
    NormalInput,
    Select,
    InputStyle,
    TextArea,
    Table,
  },
  data() {
    return {
      FormValues: {
        FirstName: "",
        LastName: "",
        Adress: "",
        SelectedDate: "",
        Gender: "",
        Notes: "",
      },
      FormResult: [],
    };
  },
  validations() {
    return {
      FormValues: {
        FirstName: { required },
        LastName: { required },
        Adress: { required, maxLengthValue: maxLength(35) },
      },
    };
  },

  methods: {
    async SubmitForm() {
      const result = await this.v$.$validate();
      if (result) {
        this.FormResult.push({
          FirstName: this.FormValues.FirstName,
          LastName: this.FormValues.LastName,
          Adress: this.FormValues.Adress,
          SelectedDate: this.FormValues.SelectedDate,
          Notes: this.FormValues.Notes,
          Gender: this.FormValues.Gender,
        });
        console.log(this.FormResult, "first");
        alert("sucsess");
        this.Clear();
      } else {
        alert("failed to submit");
      }
    },
    Clear() {
      this.FormValues.FirstName = "";
      this.FormValues.LastName = "";
      this.FormValues.Adress = "";
      this.FormValues.SelectedDate = "";
      this.FormValues.Notes = "";
      this.FormValues.Gender = "";
    },
  },
};
</script>
<style>
body {
  padding: 50px;
}
</style>
