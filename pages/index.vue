<template>
  <div>
    <h2>Welcome to NuxtJs Boilerplate used to create this project</h2>
    <img :src="image"/>
      <ul >
   <li v-for="fact in facts" :key="fact.date">
     {{ fact.name}} on {{ fact.date}} - {{ fact.week_day}}
   </li>
  </ul>
  </div>

</template>

<script>
import fetch from "isomorphic-fetch"
import logo from "./../assets/axis-bank-logo-vector.png"
export default {
  async asyncData() {
    const response = await fetch("https://holidays.abstractapi.com/v1/?api_key=9c9a7f5235ca4da6bfb56952a7ba9c0b&country=IN&year=2020")
    const facts = await response.json()
    return  { facts }
  },
        data () {
            return {
                image: logo
            }
        }
};
</script>
