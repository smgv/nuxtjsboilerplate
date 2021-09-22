<template>
  <div>
    <h1>About Nuxt Js</h1>
    Know More About ->
    <a href="https://nuxtjs.org/" target="_blank">Get Started</a>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Nuxt Js Demo Project",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "NuxtJs Boilerplate used to create this project",
        },
      ],
    };
  },
};
</script>
