<template>
  <div>
    <SearchUsers @search-text="searchText" />
    <User
      v-for="user in users"
      :id="user.id"
      :key="user.id"
      :name="user.name"
    />
  </div>
</template>

<script>
import axios from "axios";
import User from "../../components/User";
import SearchUsers from "../../components/SearchUsers";

export default {
  components: {
    User,
    SearchUsers,
  },
  head() {
    return {
      title: `Users List`,
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
      users: [],
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
        "https://jsonplaceholder.typicode.com/users",
        config
      );
      this.users = res.data;
    } catch (err) {
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json",
        },
      };

      try {
        const res = await axios.get(
          `https://jsonplaceholder.typicode.com/users`,
          config
        );
        const { data = [] } = res;
        const filterdResult = data.filter((user) => user.name.includes(text));
        this.users = filterdResult;
      } catch (err) {
        
      }
    },
  },
};
</script>
