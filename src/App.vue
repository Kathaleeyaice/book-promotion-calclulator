<template>
  <div id="app">
    <div class="bookAll">
      <div v-for="bookData in bookList" :key="bookData.id">
        <div class="bookBox">
          <div class="bookImg">
            <img :src="bookData.image" />
          </div>
          <div class="bookName">
            {{ bookData.name }}
          </div>
          <div class="bookBoxRight">
            <div class="bookPrice">ราคา {{ bookData.price }}</div>
            <div class="bookNumber">
              จำนวน
              <button v-on:click="selectedIncrease(bookData.id)">+</button>
              {{ bookData.selectedNum }}
              <button v-on:click="selectedDecrease(bookData.id)">-</button>
              เล่ม
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="orderAll">
      <div>
        <div>
          รายการสั่งซื้อ
        </div>
        <div>รวม {{ bookTotal }} เล่ม</div>
        <div>ราคารวม {{ priceTotal }} บาท</div>
        <div>ส่วนลด {{ discount }} บาท</div>
        <div>ราคาสุทธิ {{ priceFinal }} บาท</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      bookList: [
        {
          id: 1,
          name: "แฮรี่ พอตเตอร์กับศิลาอาถรรพ์",
          image:
            "https://upload.wikimedia.org/wikipedia/th/thumb/a/a2/Hp_ps_thai.jpg/330px-Hp_ps_thai.jpg",
          price: 100,
          selectedNum: 0
        },
        {
          id: 2,
          name: "แฮร์รี่ พอตเตอร์กับห้องแห่งความลับ",
          image:
            "https://upload.wikimedia.org/wikipedia/th/thumb/f/f9/%E0%B8%AB%E0%B9%89%E0%B8%AD%E0%B8%87%E0%B9%81%E0%B8%AB%E0%B9%88%E0%B8%87%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B8%A5%E0%B8%B1%E0%B8%9A.jpg/330px-%E0%B8%AB%E0%B9%89%E0%B8%AD%E0%B8%87%E0%B9%81%E0%B8%AB%E0%B9%88%E0%B8%87%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B8%A5%E0%B8%B1%E0%B8%9A.jpg",
          price: 100,
          selectedNum: 0
        },
        {
          id: 3,
          name: "แฮร์รี่ พอตเตอร์กับนักโทษแห่งอัซคาบัน",
          image:
            "https://upload.wikimedia.org/wikipedia/th/thumb/e/ee/%E0%B8%AD%E0%B8%B1%E0%B8%8B%E0%B8%84%E0%B8%B2%E0%B8%9A%E0%B8%B1%E0%B8%99.jpg/330px-%E0%B8%AD%E0%B8%B1%E0%B8%8B%E0%B8%84%E0%B8%B2%E0%B8%9A%E0%B8%B1%E0%B8%99.jpg",
          price: 100,
          selectedNum: 0
        },
        {
          id: 4,
          name: "แฮร์รี่ พอตเตอร์กับถ้วยอัคนี",
          image:
            "https://upload.wikimedia.org/wikipedia/th/thumb/4/4f/%E0%B8%96%E0%B9%89%E0%B8%A7%E0%B8%A2%E0%B8%AD%E0%B8%B1%E0%B8%84%E0%B8%99%E0%B8%B5.jpg/330px-%E0%B8%96%E0%B9%89%E0%B8%A7%E0%B8%A2%E0%B8%AD%E0%B8%B1%E0%B8%84%E0%B8%99%E0%B8%B5.jpg",
          price: 100,
          selectedNum: 0
        },
        {
          id: 5,
          name: "แฮร์รี่ พอตเตอร์กับภาคีนกฟีนิกซ์",
          image:
            "https://upload.wikimedia.org/wikipedia/th/thumb/d/dc/%E0%B8%A0%E0%B8%B2%E0%B8%84%E0%B8%B5.jpg/330px-%E0%B8%A0%E0%B8%B2%E0%B8%84%E0%B8%B5.jpg",
          price: 100,
          selectedNum: 0
        },
        {
          id: 6,
          name: "แฮร์รี่ พอตเตอร์กับเจ้าชายเลือดผสม",
          image:
            "https://upload.wikimedia.org/wikipedia/th/thumb/8/81/%E0%B9%80%E0%B8%88%E0%B9%89%E0%B8%B2%E0%B8%8A%E0%B8%B2%E0%B8%A2%E0%B9%80%E0%B8%A5%E0%B8%B7%E0%B8%AD%E0%B8%94%E0%B8%9C%E0%B8%AA%E0%B8%A1.jpg/330px-%E0%B9%80%E0%B8%88%E0%B9%89%E0%B8%B2%E0%B8%8A%E0%B8%B2%E0%B8%A2%E0%B9%80%E0%B8%A5%E0%B8%B7%E0%B8%AD%E0%B8%94%E0%B8%9C%E0%B8%AA%E0%B8%A1.jpg",
          price: 100,
          selectedNum: 0
        },
        {
          id: 7,
          name: "แฮร์รี่ พอตเตอร์กับเครื่องรางยมทูต",
          image:
            "https://upload.wikimedia.org/wikipedia/th/a/aa/Harrypotterandthedeathlyhallows.jpg",
          price: 100,
          selectedNum: 0
        }
      ],
      bookTotal: 0,
      priceTotal: 0,
      discount: 10,
      priceFinal: 0
    };
  },
  components: {},
  methods: {
    selectedIncrease(id) {
      this.bookList[id - 1].selectedNum += 1;
      this.bookTotal += 1;
      this.findTotalPrice();
      this.findPriceFinal();
    },
    selectedDecrease(id) {
      if (this.bookList[id - 1].selectedNum > 0) {
        this.bookList[id - 1].selectedNum -= 1;
        this.bookTotal -= 1;
        this.findTotalPrice();
        this.findPriceFinal();
      }
    },
    findTotalPrice() {
      this.priceTotal = 0;
      for (let i = 0; i < this.bookList.length; i++) {
        this.priceTotal +=
          this.bookList[i].selectedNum * this.bookList[i].price;
      }
    },
    findPriceFinal() {
      this.priceFinal = this.priceTotal - this.discount;
    }
  }
};
</script>

<style>
#app {
  display: inline-flex;
}
.bookAll {
  display: inline-block;
}
.book {
  display: inline-block;
}
.bookBox {
  display: inline-flex;
  width: auto;
  border: solid;
}
.bookImg {
  margin: 5px 35px 5px 35px;
}
img {
  width: 120px;
  height: 150px;
}
.bookName {
  width: 260px;
  margin: 5px 35px 5px 35px;
}
.bookBoxRight {
  margin: 5px 35px 5px 35px;
}
</style>
