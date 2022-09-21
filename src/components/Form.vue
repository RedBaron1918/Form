<template>
  <form class="row g-4">
    <div class="col-md-5">
      <label class="form-label">First name</label>
      <input
        type="text"
        class="form-control"
        :value="FirstName"
        @input="$emit('update:FirstName', $event.target.value)"
        required
      />
    </div>
    <div class="col-md-5">
      <label class="form-label">Last name</label>
      <input
        type="text"
        class="form-control"
        :value="LastName"
        @input="$emit('update:LastName', $event.target.value)"
        required
      />
    </div>
    <div class="col-10">
      <label class="form-label">adress</label>
      <input
        type="text"
        class="form-control"
        :value="Adress"
        @input="$emit('update:Adress', $event.target.value)"
        maxlength="35"
        required
      />
    </div>
    <div class="col-md-3">
      <label class="form-label">Date of Birth</label>
      <input type="date" class="form-control" />
    </div>

    <div class="col-md-3">
      <label class="form-label">Select Gender</label>
      <select class="form-select">
        <option selected disabled value="">Choose...</option>
        <option value="male">Male</option>
        <option value="female">female</option>
      </select>
    </div>

    <div class="col-10">
      <div class="form-floating">
        <textarea
          class="form-control"
          placeholder="Leave a comment here"
          style="height: 100px"
        ></textarea>
        <label for="floatingTextarea2">Comments</label>
      </div>
    </div>
    <div class="col-12">
      <button class="btn btn-primary" type="submit" @click.prevent="stuff">
        Submit form
      </button>
    </div>
  </form>
</template>

<script>
export default {
  props: ["FirstName", "LastName", "Adress"],
  emits: ["update:FirstName", "update:LastName", "print", "update:Adress"],
  methods: {
    stuff() {},
  },
};
</script>

<style></style>
