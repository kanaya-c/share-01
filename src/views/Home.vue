<template>
  <div class="flex">
    <div class="left">
      <!-- <div class="left-padding">
        <img  class="logo" src="../assets/logo.png" alt="">
        <div class="flex icon-field">
          <img class="icon" src="../assets/home.png" alt="">
          <p>ホーム</p>
        </div>
        <div class="flex icon-field">
          <img class="icon" src="../assets/profile.png" alt="">
          <p>プロフィール</p>
        </div>
        <div class="flex icon-field">
          <img class="icon" src="../assets/logout.png" alt="">
          <p>ログアウト</p>
        </div>
      </div>
      <hr />
      <div class="share">
        <p>シェア</p>
        <textarea></textarea>
        <div>
          <button>シェアする</button>
        </div>
      </div>
    </div>
    <div class="right">
      <div class="title">
        <p>ホーム</p>
      </div>
      <div v-for="(value, key, index) in shares" :key="index">
        <div class="message">
          <div class="flex">
            <p class="name">{{value.name}}</p>
            <img class="icon" src="../assets/heart.png" alt="">
            <p class="number">{{value.like.length}}</p>
            <img class="icon" src="../assets/cross.png" alt="">
            <img class="icon detail" src="../assets/detail.png" alt="">
          </div>
          <p class="text">{{value.share}}</p>
        </div>
      </div> -->
      <SideNavi />
    </div>
    <div class="right">
      <div class="title">
        <p>ホーム</p>
      </div>
      <Message />
    </div>
  </div>
</template>

<script>
// export default {
//   data() {
//     return {
//       shares: [{name: "太郎", like: [], share: "初めまして" }]
//     };
//   }
// };
import SideNavi from "../components/SideNavi";
import Message from "../components/Message";
export default {
  components: {
    SideNavi,
    Message
  }
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

/* .left-padding {
  margin: 20px;
}
.logo {
  width: 100px;
}
.icon-field {
  margin-top: 15px;
  cursor: pointer;
}
.icon-field p {
  font-size: 16px;
  padding-left: 15px;
}
.share {
  margin: 15px;
}
.share textarea {
  width: 95%;
  height: 120px;
  margin-top: 15px;
  margin-bottom: 15px;
  border-radius: 10px;
  border: 1px solid white;
  background-color: #15202b;
  color: white;
  resize: none;
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
.header {
  text-align: center;
  margin-top: 20px;
  padding-bottom: 10px;
  border-bottom: 1px solid white;
}
.icon {
  width: 25px;
  height: 25px;
}
.detail {
  margin-left: 50px;
}
.message {
  padding: 20px;
  border-bottom: solid 1px white;
  border-left: solid 1px white;
}
.name {
  font-size: 18px;
  font-weight: bold;
  margin-right: 10px;
}
.text {
  margin-top: 10px;
}
.number {
  margin-left: 10px;
  margin-right: 10px;
} */
</style>