<template>
  <div class="flex">
    <div class="left">
      <SlideNavi />
    </div>
    <div class="right">
      <div class="title">
        <p>ホーム</p>
      </div>
      <Message :id="id" />
      <div class="comment">
        <div class="comment-title">
          <p>コメント</p>
        </div>
        <div class="message" v-for="(comment, index) in data" :key="index">
          <div class="flex">
            <p class="name">{{comment.comment_user.name}}</p>
          </div>
          <div>
            <p class="text">{{comment.comment.content}}</p>
          </div>
        </div>
        <input v-model="content" type="text">
        <div @click="send">
          <button>コメント</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SlideNavi from "../components/SideNavi";
import Message from "../components/Message";
import axios from "axios";
export default {
  props: ["id"],
  data() {
    return {
      content: "",
      data: "",
      // data: [{ name: "太郎", like: [], share: "初めまして" }]
    };
  },
  methods: {
    send() {
      axios
      .post("https://glacial-meadow-49934.herokuapp.com/api/comment", {
        share_id: this.id,
        user_id: this.$store.state.user.id,
        content: this.content,
      })
      .them((response) => {
        console.log(response);
        this.content = "";
        this.$router.go({
          path: this.$router.currentRoute.path,
          force: true,
        });
      });
    },
    comment() {
      axios
      .get("https://glacial-meadow-49934.herokuapp.com/api/shares/" +this.id)
      .then((response) => {
        this.data = response.data.comment;
      });
    },
  },
  created() {
    this.comment();
  },
  components: {
    SlideNavi,
    Message
  },
};
</script>

<style scoped>
.left {
  width: 22%;
  height: 100vh;
}
.right {
  width: 78%;
  height: 100vh;
}
.flex {
  display: flex;
}
.title {
  border-bottom: 1px solid white;
  border-left: 1px solid white;
  padding: 15px;
}
.title p {
  font-size: 20px;
  font-weight: bold;
}
.share-message {
  border-bottom: 1px solid white;
}
.commnet-title {
  text-align: center;
  padding-top: 10px;
  padding-bottom: 10px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
.commnet input {
  width: 95%;
  height: 30px;
  margin-top: 20px;
  margin-bottom: 15px;
  margin-left: 10px;
  border-radius: 10px;
  border: 1px solid white;
  background-color: #15202b;
  color: white;
}
.message {
  padding-top: 10px;
  padding-left: 10px;
  padding-bottom: 10px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
.text {
  margin-top: 10px;
  font-size: 10px;
}
button {
  width: 100px;
  text-align: center;
  padding: 8px 0 10px;
  color: #fff;
  background-color: #5419da;
  border-radius: 25px;
  display: block;
  margin: 0 0 0 auto;
}
</style>