<template>
  <div class="container">
    <h1 class="text-center">Users Table</h1>
    <table class="table table-bordered">
      <thead class="thead-light">
        <tr>
          <th>Id</th>
          <th>Firstname</th>
          <th>Lastname</th>
          <th>Age</th>
          <th>Gender</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tr v-for="user in users" :key="user.id">
        <td>{{user.id}}</td>
        <td>{{user.firstname}}</td>
        <td>{{user.lastname}}</td>
        <td>{{user.age}}</td>
        <td>{{user.gender.name}}</td>
        <td>
          <div class="row">
            <div class="col text-right">
              <font-awesome-icon icon="edit" title="Update" size="2x" class="text-warning pt-1" />
            </div>
            <div class="col text-left">
              <font-awesome-icon
                icon="trash-alt"
                title="Delete"
                size="2x"
                class="text-danger pt-1"
                @click="deleteUser(user.id, this)"
              />
            </div>
          </div>
        </td>
      </tr>
    </table>
    <div class="text-center">
      <btn class="btn btn-primary" @click="showFormAddUser">Add an user</btn>
    </div>
    <form class="p-2" v-show="formAddUserVisible">
      <div class="row">
        <div class="col">
          <input type="text" class="form-control" placeholder="First name" />
        </div>
        <div class="col">
          <input type="text" class="form-control" placeholder="Last name" />
        </div>
        <div class="col">
          <input type="number" class="form-control" placeholder="Age" min="18" />
        </div>
        <font-awesome-icon icon="check-square" title="Create" size="2x" class="text-success pt-1" />
        <font-awesome-icon
          icon="window-close"
          title="Close"
          @click="closeFormAddUser"
          size="2x"
          class="text-danger pt-1"
        />
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "UserTable",
  data() {
    return {
      users: [],
      formAddUserVisible: false
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
  },
  methods: {
    loadUserTable() {
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
    },
    showFormAddUser() {
      this.formAddUserVisible = true;
    },
    closeFormAddUser() {
      this.formAddUserVisible = false;
    },
    deleteUser(userId, item) {
      console.log(item)
      // axios
      //   .delete("http://localhost:9090/Users/" + userId)
      //   .then(response => {
      //     if (response.status === 200) {
      //       loadUserTable()
      //     }
      //   })
      //   .catch(error => {
      //     this.msg = error;
      //   });
    }
  }
};
</script>

<style lang="stylus" scoped></style>