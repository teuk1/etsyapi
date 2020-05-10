<template>
  <section>
    <b-field>
      <b-input
        v-model="keyValue"
        placeholder="Enter your Etsy apikey"
        type="text"
        @keydown.enter.native="fetch()"
      ></b-input>
    </b-field>
    <div>
      {{ info }}
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      info: null,
      keyValue: null
    };
  },
  created() {
    //this.fetch();
  },
  methods: {
    fetch() {
      axios
        .get("http://localhost:8080/listings/active?api_key=" + this.keyValue)
        .then(response => {
          console.log("++++ SUCCESS ++++");
          this.info = response;
        })
        .catch(() => {
          console.log("---- ERROR ----");
        });
    }
  }
};
</script>

<style lang="less"></style>
