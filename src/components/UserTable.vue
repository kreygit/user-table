<template>
  <div class="container">
    <h1 class="text-center">Tableau d'utilisateurs</h1>
    <table class="table table-sm table-bordered">
      <thead class="thead-light">
        <tr>
          <th>Id</th>
          <th>Firstname</th>
          <th>Lastname</th>
          <th>Age</th>
          <th>Gender</th>
        </tr>
      </thead>
      <tr v-for="user in users" :key="user.id">
        <td>{{user.id}}</td>
        <td>{{user.firstname}}</td>
        <td>{{user.lastname}}</td>
        <td>{{user.age}}</td>
        <td>{{user.gender.name}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "UserTable",
  data() {
    return {
      users: []
    };
  },
  beforeCreate() {
    axios
      .get("http://localhost:9090/Users")
      .then(response => {
        if (response.status === 200) {
          this.users = response.data;
        }
      })
      .catch(error => {
        this.msg = error;
      });
  }
};
</script>

<style lang="stylus" scoped></style>