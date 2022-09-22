<template>
  <div class="table-responsive mt-2">
    <table class="table align-middle">
      <thead class="table-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">First Name</th>
          <th scope="col">Last Name</th>
          <th scope="col">Address</th>
          <th scope="col">Date</th>
          <th scope="col">Gender</th>
          <th scope="col">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for:="(data, index) in FormResult" style="cursor: pointer">
          <th scope="row" @click="popup(data.Notes)">
            {{ index + 1 }}
          </th>
          <td @click="popup(data.Notes)">{{ data.FirstName }}</td>
          <td @click="popup(data.Notes)">{{ data.LastName }}</td>
          <td @click="popup(data.Notes)">{{ data.Adress }}</td>
          <td @click="popup(data.Notes)">{{ data.SelectedDate }}</td>
          <td @click="popup(data.Notes)">{{ data.Gender }}</td>
          <td>
            <button
              type="button"
              class="btn btn-danger"
              @click="$emit('RemoveItem', data)"
            >
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
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
