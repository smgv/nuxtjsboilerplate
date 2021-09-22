<template>
  <div>
    <form>
      <input v-model="text" type="text" placeholder="Search Users..." />
    </form>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "SearchUsers",
  data() {
    return {
      text: "",
    };
  },
  watch: {
    text() {
      this.$emit("search-text", this.text);
    },
  },
});
</script>
