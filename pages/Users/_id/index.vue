<template>
  <div>
    <nuxt-link to="/users">Back To User List</nuxt-link>
    <hr />
    <div>
      <p>Name: {{ user.name }}</p>
      <p>Phone No: {{ user.phone }}</p>
      <p>Email Id: {{ user.email }}</p>
      <p>Email Id: {{ user.email }}</p>
    </div>
    <hr />
    <small>User ID: {{ $route.params.id }}</small>
  </div>
</template>

<script>
import axios from "axios";

export default {
  head() {
    return {
      title: `User - ${this.user.name}`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "NuxtJs Boilerplate used to create this project",
        },
      ],
    };
  },
  data() {
    return {
      user: {},
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };

    try {
      const res = await axios.get(
        `https://jsonplaceholder.typicode.com/users?id=${this.$route.params.id}`,
        config
      );
      const { data = [] } = res;
      this.user = data[0];
    } catch (err) {
    }
  },
};
</script>
