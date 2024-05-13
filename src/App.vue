<template>
  <h2>Add User</h2>
  <div class="container">
      <div class="input-group flex-nowrap">
          <span class="input-group-text" id="addon-wrapping">Your Name</span>
          <input type="text" class="form-control" v-model="fullname" placeholder="Username" aria-label="Username" aria-describedby="addon-wrapping">
          <p class="text-danger" v-if="fullname.length === 0">Name is required!</p>
          <p class="text-danger" v-else-if="fullname.length < 8">Name should have at least 8 characters!</p>
          <p class="text-success" v-else>Success!</p>
      </div>
      <div class="input-group flex-nowrap my-3">
          <span class="input-group-text" id="addon-wrapping">Your Email</span>
          <input type="text" class="form-control" v-model="email" placeholder="Username" aria-label="Username" aria-describedby="addon-wrapping">
          <p class="text-danger" v-if="email.length === 0">Email is required!</p>
          <p class="text-danger" v-else-if="!email.includes('@')">Email should contain '@'!</p>
          <p class="text-danger" v-else-if="email.length < 5">Email should have at least 5 characters!</p>
          <p class="text-success" v-else>Success!</p>
      </div>
      <button class="btn btn-primary my-3 m-1" @click="saveTask()">Create User</button>
      <table class="table caption-top">
          <thead>
              <tr>
                  <th scope="col">ID</th>
                  <th scope="col">First Name</th>
                  <th scope="col">Email</th>
                  <th scope="col">Action</th>
              </tr>
          </thead>
          <tbody>
              <tr v-for="(user, index) in profile" :key="index">
                  <th scope="row">{{index + 1}}</th>
                  <td>{{ user.fullname }}</td>
                  <td>{{ user.email }}</td>
                  <td id="c-btn">
                      <button class="btn btn-danger" @click="deleteUser(index)">Delete</button>
                  </td>
              </tr>
          </tbody>
      </table>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
      return {
          fullname: "",
          email: "",
          profile: [
              { fullname: "Chuon Veasna", email: "chuonveasna123@gmail.com" },
              { fullname: "Chuon Veasna", email: "chuonveasna123@gmail.com" },
              { fullname: "Chuon Veasna", email: "chuonveasna123@gmail.com" },
          ],
      };
  },
  methods: {
      deleteUser(index) {
          this.profile.splice(index, 1);
      },
      saveTask() {
          if (this.fullname.length >= 8 && this.email.length >= 5 && this.email.includes('@')) {
              this.profile.push({ fullname: this.fullname, email: this.email });
              this.fullname = "";
              this.email = "";
          } else {
              console.log("Validation failed");
          }
      }
  }
};
</script>

<style>

</style>
