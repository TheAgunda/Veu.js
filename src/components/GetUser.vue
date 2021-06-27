<template>
  <table>
    <thead>
      <th>Title</th>
      <th>First name</th>
      <th>last name</th>
      <th>Email</th>
      <th>Image</th>
    </thead>
    <tbody>
      <tr v-for="item in list" v-bind:key="item.id">
        <td>{{ item.name.title }}</td>
        <td>{{ item.name.first }}</td>
        <td>{{ item.name.last }}</td>
        <td>{{ item.email }}</td>
        <td>{{ item.picture.large }}</td>
      </tr>
    </tbody>
  </table>
</template>
<script>
import axios from "axios";
export default {
  name: "GetUser",
  data() {
    return { list: undefined };
  },
  //Document ready
  async mounted() {
    let result = await axios.get("https://randomuser.me/api/");
    console.log(result.data.results);
    this.list = result.data.results;
  },
};
</script>
<style scoped>
table {
  border: 1px solid grey;
  border-spacing: 0px;
}
th {
  border-bottom: 1px solid grey;
  padding: 0.5rem;
}
td {
  border-bottom: 1px solid grey;
  padding: 0.5rem;
}
</style>
