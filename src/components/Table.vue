<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">First Name</th>
        <th scope="col">Last Name</th>
        <th scope="col">Address</th>
        <th scope="col">Date</th>
        <th scope="col">Gender</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for:="(data, index) in FormResult"
        @click="popup(data.Notes)"
        style="cursor: pointer"
      >
        <th scope="row">
          {{ index + 1 }}
        </th>
        <td>{{ data.FirstName }}</td>
        <td>{{ data.LastName }}</td>
        <td>{{ data.Adress }}</td>
        <td>{{ data.SelectedDate }}</td>
        <td>{{ data.Gender }}</td>
        <td>
          <button
            type="button"
            class="btn btn-danger"
            @click="$emit('RemoveItem', data)"
          >
            Danger
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["FormResult"],
  methods: {
    popup(item) {
      alert(item);
    },
    // RemoveForm(form) {
    //   this.FormResult = this.FormResult.filter((item) => {
    //     return form !== item;
    //   });
    // },
  },
};
</script>

<style></style>
