<template>
  <div class="content">
    <div @click="updateJoke" class="fold page">
      <div class="txt-body">
        {{ txt.text }}
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import firebase from "../firebaseConfig";
const db = firebase.firestore();
export default {
  name: "Joke",
  data() {
    return {
      txt: {
        id: -1,
        text: "Joke Pending",
      },
      jokes: [],
    };
  },
  methods: {
    updateJoke() {
      console.log("Gettting new joke");
      let temp = 0;
      // eslint-disable-next-line no-constant-condition
      while (true) {
        temp = Math.floor(Math.random() * this.jokes.length);
        // console.log(this.jokes[temp].id);
        // console.log(this.txt.id);
        if (this.txt.id !== this.jokes[temp].id) break;
      }
      // console.log(temp);
      this.txt = this.jokes[temp];
      // console.log(this.txt);
    },
    getJoke() {
      axios
        .get("https://api.coindesk.com/v1/bpi/currentprice.json")
        .then((response) => (this.txt = response.data.bpi))
        .catch((err) => {
          console.log(err);
          this.txt = "try again later";
        });
    },
    getJokes() {
      this.jokes = [];
      db.collection("jokes")
        .get()
        .then((snapshot) => {
          snapshot.forEach((doc) => {
            this.jokes.push({
              id: doc.id,
              text: doc.data().text,
            });
            // console.log(doc.id, " => ", doc.data().text);
          });
          this.updateJoke();
        })
        .catch((error) => {
          console.log("Error", error);
        });
    },
  },
  mounted() {
    // this.getJoke();
    this.getJokes();
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
  font-size: 2em;
}

/* 

https://codepen.io/muhamidelsayed/pen/rjyMaM
 */
/* paper */
.fold {
  height: 100%;
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
  border-width: 0 1.5em 1.5em 0;
  border-color: #eee #344;
}</style
>>
