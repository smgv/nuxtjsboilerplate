<template>
  <div>
    <h2>Welcome to NuxtJs Boilerplate used to create this project</h2>
    <img :src="image"/>
      <ul >
   <li>
    App {{ data.name}} version {{ data.version}} - description {{ data.description}}
   </li>
  </ul>
  </div>

</template>

<script>
import fetch from "isomorphic-fetch"
import logo from "./../assets/axis-bank-logo-vector.png"
export default {
  async asyncData() {
    const response = await fetch("https://leap.api.axisbank.com/version")
    const  { data } = await response.json()
    return  { data }
  },
        data () {
            return {
                image: logo
            }
        }
};
</script>
