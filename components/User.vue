<template>
  <nuxt-link :to="'users/' + id">
    <div class="user">
      <p>{{ name }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "User",
  props:["name", "id"],
};
</script>

<style>
.user {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>
