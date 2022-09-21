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
      <tr v-for:="(data, index) in FormResult">
        <th scope="row">{{ index + 1 }}</th>
        <td>{{ data.FirstName }}</td>
        <td>{{ data.LastName }}</td>
        <td>{{ data.Adress }}</td>
        <td>{{ data.SelectedDate }}</td>
        <td>{{ data.Gender }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["FormResult"],
};
</script>

<style></style>
