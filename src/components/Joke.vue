<template>
  <div class="content">
    <div @click="updateJoke" class="fold page">
      <div class="txt-body">
        {{ txt }}
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Joke",
  data() {
    return {
      txt: null,
    };
  },
  methods: {
    updateJoke() {
      console.log("Gettting new joke");
    },
    getJoke() {
      axios
        .get("https://api.coindesk.com/v1/bpi/currentprice.json")
        .then((response) => (this.txt = response))
        .catch((err) => {
          console.log(err);
          this.txt = "Joke Pending";
        });
    },
  },
  mounted() {
      axios
        .get("https://api.coindesk.com/v1/bpi/currentprice.json")
        .then((response) => (this.txt = response))
        .catch((err) => {
          console.log(err);
          this.txt = "Joke Pending";
        });
  },
};


</script>

<style scoped>
.page {
  display: flex;
  justify-content: center;
  align-items: center;
  background: burlywood;

  /* height: 100vh; */
}
.content {
  /* position: relative; */
  background: #344;
  padding: 2em;
  height: 100vh;
}

.txt-body {
  color: coral;
  font-size: 1.2em;
}

/* 

https://codepen.io/muhamidelsayed/pen/rjyMaM
 */
/* paper */
.fold {
  height: 100%;
  /* margin: 1px; */
  /* position: absolute; */
  /* height: 200px; */
  /* padding: 25px; */
  background: #fff;
}
/* folding */
.fold::before {
  content: "";
  position: absolute;
  top: 2em;
  right: 2em;
  border-style: solid;
  /* border-width: 0 100px 100px 0; */
  border-width: 0;
  border-right-width: 100px;
  border-bottom-width: 100px;
  /* border-color: #ddd #344; */
  border-bottom-color: #ddd;
  border-right-color: #344;
  transition: all ease 0.5s;
}
.fold:hover::before {
  border-width: 0 10em 10em 0;
  border-color: #eee #344;
}</style
>>
