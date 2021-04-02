<template>
  <div class="hello">
    <select v-model="select">
      <option v-for="(gender, index) in genders" :key="index" :value="gender">
        {{ gender }}
      </option>
    </select>
    <br />
    <input type="text" v-model="search" />
    <ul>
      <li v-for="member in filterMembers" :key="member.id">
        {{ member.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      search: "",
      select: "",
      genders: ["Male", "Female"],
      members: [
        {
          name: "Neo",
          id: 5,
          gender: "Male",
        },
        {
          name: "Trinity",
          id: 2,
          gender: "Female",
        },
        {
          name: "Morpheous",
          id: 3,
          gender: "Male",
        },
        {
          name: "Neoa",
          id: 4,
          gender: "Female",
        },
      ],
    };
  },
  computed: {
    filterMembers: function () {
      let filtered = this.members;
      if (this.search) {
        filtered = this.members.filter(
          (m) => m.name.toLowerCase().indexOf(this.search) > -1
        );
      }
      if (this.select) {
        filtered = filtered.filter(
          (m) => m.gender.toLowerCase() === this.select.toLowerCase()
        );
      }
      return filtered;
    },
  },
};
</script>

<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
