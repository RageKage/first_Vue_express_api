<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2 >{{ helloMessage = `Welcome to my Page, ${name}`}}</h2>
    <div>
      <label for="name">Enter your name: </label> <br>
      <input v-model="name" id="name" />
      <p v-if="name">
        <button v-on:click="Clear">Clear</button>
      </p>

    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      helloMessage: "",
      name: "",
    };
  },
  methods: {
    Clear() {
      this.name = "";
    },
  },
  props: {
    msg: String,
  },
  mounted() {
    this.$hello_api.getHelloMessage().then((resp) => {
      // console.log(resp)
      this.helloMessage = resp.message;
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
