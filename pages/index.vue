<template>
  <div>
    <h2>Welcome to NuxtJs Boilerplate used to create this project</h2>
    <img :src="image" />
    <ul id="example-1">
      <li v-for="item in data" :key="item.message">
        <img :src="item.description[0].iconURL" />
        {{ item.description[0].text }}
        <p>Using v-html directive: <span v-html="item.productTnC"></span></p>
        <br />
      </li>
    </ul>
  </div>
</template>

<script>
import fetch from "isomorphic-fetch";
import logo from "./../assets/axis-bank-logo-vector.png";
import https from "https";
export default {
  async asyncData() {
    const httpsAgent = new https.Agent({
      rejectUnauthorized: false,
    });

    const response = await fetch(
      "https://leap.api.dev.axisb.com/saving-account/get-products",
      {
        headers: {
          "Content-Type": "application/json",
          "x-api-key":
            "y6L1qGcdakovpt::eba37aa536db7e66be491b986c94563c5824886541dd3b69",
        },
        agent: httpsAgent,
      }
    );
    const { data } = await response.json();
    return { data };
  },
  data() {
    return {
      image: logo,
    };
  },
};
</script>
