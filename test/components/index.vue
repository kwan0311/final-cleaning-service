<template>
  <div class="middle">
    <div class="middle_item">
      <img src="../img/man.png" alt="" />
      <div>
        <p>Start searching today</p>
        <p>and find the best</p>
        <p>cleaner for you</p>
        <div class="btn">Start Cleanning Trip</div>
      </div>
    </div>
    <div class="line"></div>
    <div class="middle_item">
      <div>
        <p>Know our team,our</p>
        <p>best backup</p>
        <div class="btn">About Us</div>
      </div>
      <img src="../img/woman.png" alt="" />
    </div>
    <div class="line"></div>
    <div class="middle_item">
      <img src="../img/man1.png" alt="" />
      <div>
        <p>your idea is our best</p>
        <p>way to improve</p>
        <div class="btn">About</div>
      </div>
    </div>
    <div class="line" style="width: 50%"></div>
  </div>
</template>

<script>
module.exports = {};
</script>

<style scoped>
.middle {
  width: 80%;
  margin: 20px auto;
}
.middle_item {
  /* height: 300px; */
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: space-around;
  font-weight: bold;
  font-size: calc(100vw / 60);
}
.middle_item img {
  height: calc(100vw * 0.3);
  /* height: 280px; */
  border-radius: 20px;
  box-shadow: 2px 2px 12px #000;
  /* margin-right: 100px; */
}
.middle_item img:nth-child(2) {
  margin-right: 0px;
}
.btn {
  padding: 10px 20px;
  background: #b1ffcc;
  text-align: center;
  border-radius: 10px;
  box-shadow: 2px 2px 12px #ccc;
  margin: 0px auto;
  margin-top: 10px;
  cursor: pointer;
}
.line {
  width: 25%;
  height: 2px;
  background: #ba9676;
  margin: 30px auto;
}
</style>