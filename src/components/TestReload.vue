<template>
  <div>
    <span>person.name: {{ person.name }}</span>
    <br />
    <span>person.nickname: {{ person.nickname }}</span>
    <br />
    <span>person.address: {{ person.address }}</span>
    <br />
    <br />
    <button
      @click="changeName"
    >this.person.name = 'Arantes'; (will auto update because `name` was in `data`)</button>
    <br />
    <button
      @click="changeNickname"
    >this.person.nickname = 'Pele'; (will NOT auto update because `nickname` was not in `data`)</button>
    <br />
    <button
      @click="changeNicknameProperly"
    >Vue.set(this.person, 'address', '99th st.'); (WILL auto update even though `address` was not in `data`)</button>
    <br />
    <br />For more info, read the comments in the code. Or check the docs on
    <b>Reactivity</b> (link below).
  </div>
</template>

<script>
export default {
  name: "TestReload",
  data() {
    return {
      person: {
        name: "Edson"
      }
    };
  },
  methods: {
    changeName() {
      // because name is declared in data, whenever it
      // changes, Vue automatically updates
      this.person.name = "Arantes";
    },
    changeNickname() {
      // because nickname is NOT declared in data, when it
      // changes, Vue will NOT automatically update
      this.person.nickname = "Pele";
      // although if anything else updates, this change will be seen
    },
    changeNicknameProperly() {
      // when some property is NOT INITIALLY declared in data, the correct way
      // to add it is using Vue.set or this.$set
      Vue.set(this.person, "address", "123th avenue.");

      // subsequent changes can be done directly now and it will auto update
      this.person.address = "345th avenue.";
    }
  }
};
</script>
<style scoped>
span:nth-of-type(1),
button:nth-of-type(1) {
  color: blue;
}
span:nth-of-type(2),
button:nth-of-type(2) {
  color: red;
}
span:nth-of-type(3),
button:nth-of-type(3) {
  color: green;
}
span {
  font-family: monospace;
}
</style>