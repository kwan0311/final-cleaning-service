<template>
  <div class="bodys">
    <div class="mask" v-if="middleH"></div>
    <div class="top">
      <div>
        <img src="../img/left.png" alt="" @click="$router.push('/home')" />
      </div>
      <div class="top_middle_H5">
        <div
          @click="middleH = !middleH"
          style="display: flex; align-items: center"
        >
          {{ currentName }} &nbsp;<img
            src="../img/up.png"
            alt=""
            v-if="middleH"
          /><img v-else src="../img/dwon.png" alt="" />
        </div>
        <div class="top_middle_H5C" v-if="middleH">
          <p
            @click="
              $router.push('/home');
              middleH = !middleH;
            "
          >
            Home
          </p>
          <p
            @click="
              $router.push('/service');
              middleH = !middleH;
            "
          >
            Service
          </p>
          <p
            @click="
              $router.push('/about');
              middleH = !middleH;
            "
          >
            About
          </p>
        </div>
      </div>
      <div class="top_middle">
        <p @click="$router.push('/home')">Home</p>
        <p @click="$router.push('/service')">Service</p>
        <p @click="$router.push('/about')">About</p>
      </div>
      <div class="top_right">
        {{ userName }}
        <img src="../img/spongebob.png" alt="" />
      </div>
    </div>
    <transition
      v-bind:css="false"
      @before-enter="beforeEnter"
      @enter="enter"
      @leave="leave"
    >
       <keep-alive> <!--//store the data and avoid rendering -->
        <router-view></router-view>
      </keep-alive>
    </transition>
    <div class="footer">
      <p>Hire Us</p>
      <p>We always believe that you will find the most suitable cleaner here</p>
      <p>Contact Us</p>
      <p>(61) 4313131313</p>
      <myfooter infos="SIT120Kaiyuan@abc.com.au"></myfooter>
    </div>
  </div>
</template>
<script>
module.exports = {
  data() {
    return {
      userName: "",
      currentName: "Home",
      middleH: false,
      fadeInDuration: 1000,
      fadeOutDuration: 1000,
    };
  },
  watch: {
    $route: {
      handler: function (val, oldVal) {
        this.currentName = val.name;
      },
      // window size< 660, menu change
      //to drop down menu and title 
      //print on the nav-bar
      deep: true,
    },
  },

  mounted() {//vue life circle hook
    if (sessionStorage.getItem("userName"))
      this.userName = sessionStorage.getItem("userName");
  },
  methods: {
    beforeEnter: function (el) {
      el.style.opacity = 0;
    },
    enter: function (el, done) {
      var vm = this;
      Velocity(
        el,
        { opacity: 1 },
        {
          duration: this.fadeInDuration,
          complete: function () {
            done();
          },
        }
      );
    },
    leave: function (el, done) {
      var vm = this;
      Velocity(
        el,
        { opacity: 0 },
        {
          duration: this.fadeOutDuration,
          complete: function () {
            done();
          },
        }
      );
    },
  },
};
</script>
<style scoped>
@media only screen and (max-width: 660px) {
  .top_middle_H5 {
    width: 80%;
    display: block !important;
    display: flex !important;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  .mask {
    z-index: 99;
    position: fixed;
    top: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.5) !important;
  }
  .top_middle_H5C {
    z-index: 100;
    position: absolute;
    top: 50px;
    display: flex;
    line-height: 50px;
    flex-direction: column;
    background: #fff;
    width: 140%;
    text-align: center;
  }

  .top_middle_H5 p {
    border-bottom: 1px solid #c9c9c9;
  }
  .top_middle_H5 img {
    height: 20px !important;
  }
  .top_middle {
    display: none !important;
  }
}

.top_middle_H5 {
  display: none;
}
.bodys {
  padding: 20px 0;
}
.top {
  z-index: 100;
  background: #fff;
  display: flex;
  justify-content: space-between;
  width: 80%;
  height: 50px;
  margin: 0px auto;
  padding-left: 4%;
  border-radius: 20px;
}
.top img {
  height: 100%;
  cursor: pointer;
}
.top_middle {
  display: flex;
  justify-content: space-around;
  width: 80%;
  line-height: 50px;
  font-weight: bold;
}
.top_middle p {
  cursor: pointer;
}
.top_right {
  display: flex;
  align-items: center;
  border-radius: 20px;
}
.top_right img {
  border-radius: 20px;
}
.footer {
  text-align: center;
  color: #999aaa;
}
.footer p:nth-child(1) {
  font-weight: bold;
  font-size: 24px;
  margin: 20px 0;
  color: #000;
}
.footer p:nth-child(2) {
  margin-bottom: 30px;
}
.icons {
  width: 150px;
  display: flex;
  justify-content: space-between;
  margin: 0px auto;
  margin-top: 10px;
}
.icons img {
  width: 30px;
}
</style>