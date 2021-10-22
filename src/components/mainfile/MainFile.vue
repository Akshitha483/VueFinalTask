<template>
  <h2 style="text-align:left;">Shopping Cart</h2>
  <div class="container-main">
    <div class="box" v-for="(user, index) in apiData" :key="index">
      <img
        :src="user.image"
        @click="getDetails(user), scrollToTop()"
        :userdetails="user"
      />
      <p class="info" v-html="user.title"></p>
      <p class="info" style="font-weight: 700">Price:{{ user.price }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "main",
  data() {
    return {
      apiData: [],
    };
  },

  methods: {
    getDetails(user) {
      this.$router.push({
        name: "details",
        params: { id: user.id, details: JSON.stringify(user) },
      });
    },
    scrollToTop() {
      window.scrollTo(0, 0);
    },
  },

  async created() {
    console.log("main");
    const response = await fetch("https://fakestoreapi.com/products");
    const result = await response.json();
    console.log("result", result);
    this.apiData = result;
    console.log("apiData", this.apiData);
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.container-main {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  background-color: white;
}
.box {
  margin: 10px;
  align-items: center;
  width: auto;
  height: auto;
  border: ridge;
  background-color: white;
}
img {
  border: 5px white;
  width: 250px;
  margin: 40px auto;
  cursor: pointer;
}
h2 {
  align-content: initial;
  font-size: 40px;
  color: maroon;
}
.info {
  color: #02020a;
  font-size: larger;
}
</style>
