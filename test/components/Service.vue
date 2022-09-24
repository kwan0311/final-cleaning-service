<template>
  <div>
    <div class="middle">
      <p class="middle_h1">Start Your Service Today</p>
      <div class="middle_form">
        <div class="middle_form_item">
          <p>How big is your room?</p>
          <div>
            <input
              type="radio"
              id="radio-1-1"
              name="radio-1-set"
              checked=""
            /><label for="radio-1-1">0-80m*2</label>
          </div>
          <div>
            <input type="radio" id="radio-1-2" name="radio-1-set" /><label
              for="radio-1-2"
              >81-160m*2</label
            >
          </div>
          <div>
            <input type="radio" id="radio-1-3" name="radio-1-set" /><label
              for="radio-1-3"
              >160m*2 +</label
            >
          </div>
        </div>
        <div class="middle_form_item">
          <p>Where you live?</p>
          <select>
            <option value=""></option>
            <option value="city">Melbourne City</option>
            <option value="burwood">Burwood</option>
            <option value="altona">Altona</option>
            <option value="Boc">Box Hill</option>
            <option value="Clayton">Clayton</option>
            <option value="Richmond">Richmond</option>
          </select>
        </div>
        <div class="middle_form_item">
          <p>Language Speaking</p>
          <select> 
            <option value=""></option>
            <option value="English">English</option>
            <option value="French">French</option>
            <option value="Mandarin">Mandarin</option>
            <option value="Japanese">Japanese</option>
            <option value="Vietnamese">Vietnamese</option>
            <option value="Cantonese">Cantonese</option>
          </select>
        </div>
        <div class="btn">Start Searching</div>
        <div class="ridingLantern">
          <div class="leftBtn" @click="throttle(PrevFun)">
            <img src="../img/lefts.png" alt="" />
          </div>
          <div class="rightBtn" @click="throttle(NextFun)">
            <img src="../img/right.png" alt="" />
          </div>

          <div
            class="SwiperBox"
            @mouseenter="MouseFun('enter')"
            @mouseleave="MouseFun('leave')"
          >
            <div
              class="imgBox"
              :style="{ left: `-${leftVal}px`, transition: `${ition}s` }"
            >
              <img
                :src="item.imgUrl"
                v-for="(item, index) in imgList"
                :key="index"
              />
              <img :src="imgList[0].imgUrl" alt="" />
            </div>
          </div>
          <div class="ridingLantern_p">
            <p><span>Name:</span>Jane</p>
            <p><span>Speaking Language:</span>English</p>
            <p><span>Clean type:</span>Daily house clean, End rent clean</p>
            <p>4.85</p>
          </div>
        </div>
        <div class="btn">Start Cleanning Trip</div>
      </div>
    </div>
  </div>
</template>
  
  <script>
module.exports = {
  data() {
    return {
      imgList: [
        {
          imgUrl: "../img/woman.png",
        },
        {
          imgUrl: "../img/woman1.png",
        },
        {
          imgUrl: "../img/woman2.png",
        },
      ],
      leftVal: 0,
      flag: true,
      start: null,
      imgWidth: 300,
      ition: 1,
      imgShow: 0,
    };
  },
  mounted() {
    this.startUp();
  },
  methods: {
    MouseFun(type) {
      type == "enter" ? clearTimeout(this.start) : this.startUp();
    },
    startUp() {
      this.start = setInterval(() => {
        this.NextFun();
      }, 1500);
    },
    throttle(fun) {
      if (this.flag) {
        this.flag = false;
        fun();
        setTimeout(() => {
          this.flag = true;
        }, 1200);//prevent user click too quickly, 
        //set the gap time to 1.2 seconds
      }
    },
    PrevFun() {
      if (this.leftVal == 0) {
        this.ition = 0;
        this.imgShow = this.imgList.length - 1;
        this.leftVal = this.imgList.length * this.imgWidth;
        setTimeout(() => {
          this.ition = 0.8;
          this.leftVal -= this.imgWidth;
        }, this.ition * 1000);
      } else {
        this.ition = 0.8;
        this.leftVal -= this.imgWidth;
        this.imgShow--;
      }
    },
    NextFun() {//
      if (this.leftVal == (this.imgList.length - 1) * this.imgWidth) {
        this.ition = 0.8;
        this.leftVal += this.imgWidth;//The three pictures are arranged side by side. This method is used to offset the pictures, and then the second picture appears
        this.imgShow = 0;
        setTimeout(() => {
          this.ition = 0;
          this.leftVal = 0;
        }, this.ition * 1000);//move every 1 seconds
      } else {
        this.ition = 0.8;
        this.leftVal += this.imgWidth;
        this.imgShow++;
      }
    },
    instFun(index) {
      this.ition = 0.8;
      this.leftVal = index * this.imgWidth;
      this.imgShow = index;
    },
  },
};
</script>
  <style scoped>
.middle {
  width: 90%;
  margin: 0px auto;
  overflow: hidden;
}
.middle_form {
  width: 100%;
  background: #fff;
  border-radius: 20px;
  padding: 2%;
  display: flex;
  justify-content: center;
  flex-direction: column;
  box-sizing: border-box;
}
.middle_form_item {
  display: flex;
  padding-bottom: 2%;
}
.middle_form_item select {
  width: 100px;
  box-shadow: 2px 2px 5px #000;
}
.middle_form_item P {
  width: 200px;
  min-width: 150px;
  text-align: right;
  margin-right: 5%;
}
.middle_form_item label {
  margin-right: 20px;
  color: #999aaa;
}
.middle_h1 {
  padding: 20px 0;
  font-size: 24px;
  font-weight: bold;
  text-align: center;
}
.btn {
  padding: 10px 20px;
  background: #b1ffcc;
  text-align: center;
  border-radius: 10px;
  box-shadow: 2px 2px 12px #ccc;
  margin: 10px auto;
  cursor: pointer;
}
.ridingLantern {
  box-sizing: border-box;
  min-width: 320px;
  width: 60%;
  background: #f2e6e6;
  margin: 30px auto;
  padding: 10px;
  position: relative;
}

.SwiperBox {
  position: relative;
  margin: 0 auto;
  width: 300px;
  height: 294px;
  box-sizing: border-box;
  cursor: pointer;
  overflow: hidden;
}
.imgBox {
  position: absolute;
  top: 0px;
  left: 0px;
  min-width: 300px;
  height: 294px;
  display: flex;
  justify-content: flex-start;
}
.imgBox img {
  flex-shrink: 0;
  width: 245px;
  height: 294px;
  margin: 20px 27.5px;
}
.leftBtn,
.rightBtn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 30px;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  cursor: pointer;
  font-size: 12px;
  font-weight: 500;
  z-index: 99;
}
.leftBtn {
  left: 10px;
}
.rightBtn {
  right: 10px;
}
.leftBtn img {
  width: 100%;
}
.rightBtn img {
  width: 100%;
}
.inst {
  width: 10px;
  height: 10px;
  border: 1px solid #ccc;
  margin-right: 8px;
  background: #fff;
  border-radius: 50%;
  cursor: pointer;
}
.inst:last-child {
  margin-right: 0px;
}
.ridingLantern_p {
  width: 245px;
  text-align: center;
  margin: 10px auto;
}
.ridingLantern_p span {
  font-weight: bold;
}

@media only screen and (max-width: 660px) {
  .middle_form_item {
    margin-left: 10%;
  }
  .middle_form_item:nth-child(1) {
    flex-direction: column;
    margin-bottom: 10px;
  }

  .middle_form_item P {
    text-align: left !important;
    width: 170px !important;
  }
  .middle_form_item:nth-child(1) P {
    margin-bottom: 10px;
  }
}
</style>