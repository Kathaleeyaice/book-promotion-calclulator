<template>
  <div id="app">
    <div class="navBar">
      <div>
        <img src="./assets/bookstore.png" id="iconBookStore" />
      </div>
      <div class="bookStoreName">
        บ้านนายดิน
      </div>
    </div>
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
        <div id="order">
          รายการสั่งซื้อ
          <div>
            <img src="./assets/cart.png" id="iconCart" />
          </div>
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
          name: "แฮร์รี่ พอตเตอร์กับศิลาอาถรรพ์",
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
      discount: 0,
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
      this.findDiscount();
    },
    selectedDecrease(id) {
      if (this.bookList[id - 1].selectedNum > 0) {
        this.bookList[id - 1].selectedNum -= 1;
        this.bookTotal -= 1;
        this.findTotalPrice();
        this.findPriceFinal();
        this.findDiscount();
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
    },
    findDiscount() {
      this.discount = 0;
      let bookIDList = this.createBookIDList();
      let uniqeIDGroup = [];
      let bookIDListLength = bookIDList.length; // for constant length in loop
      for (let i = 0; i < bookIDListLength; i++) {
        let group = Array.from(new Set(bookIDList)); // create uniqe id group
        uniqeIDGroup.push(group);
        for (let j = 0; j < group.length; j++) {
          for (let k = 0; k < bookIDList.length; k++) {
            if (bookIDList[k] == group[j]) {
              bookIDList.splice(k, 1); // remove 1 element in index k
              break;
            }
          }
        }
      }
      for (let i = 0; i < uniqeIDGroup.length; i++) {
        if (uniqeIDGroup[i].length > 1) {
          for (let j = 0; j < uniqeIDGroup[i].length; j++) {
            let bookID = uniqeIDGroup[i][j] - 1;
            let discountPercent = (uniqeIDGroup[i].length - 1) * 10;
            let discount =
              (this.bookList[bookID].price * discountPercent) / 100;
            this.discount += discount;
          }
        }
      }
    },
    createBookIDList() {
      let bookIDList = [];
      for (let i = 0; i < this.bookList.length; i++) {
        for (let j = 0; j < this.bookList[i].selectedNum; j++) {
          bookIDList.push(this.bookList[i].id);
        }
      }
      return bookIDList;
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Kanit&display=swap");
body {
  font-family: "Kanit", sans-serif;
  background-color: #f8f8f8;
}
#app {
  display: inline-flex;
  width: 100%;
}
.navBar {
  width: 100vw;
  height: 5vw;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: inline-flex;
  background-color: #20639b;
  box-shadow: 2px 5px 4px rgba(0, 0, 0, 0.25);
}
#iconBookStore {
  width: 3.32667997339vw;
  height: 3.32667997339vw;
  margin: 0.66533599467vw 0 0.66533599467vw 2.32867598137vw;
}
.bookStoreName {
  color: #f8f8f8;
  font-size: 1.19760479042vw;
  font-weight: bold;
  margin: 1.66333998669vw 0 1.66333998669vw 0.66533599467vw;
}
.bookAll {
  display: inline-block;
  width: 50%;
  margin-top: 5vw;
  margin-left: 10vw;
}
.bookBox {
  display: inline-flex;
  width: 100%;
  border: none;
  margin: auto;
  margin-top: 2%;
  box-shadow: 2px 5px 4px rgba(0, 0, 0, 0.25);
  border-radius: 0.3992015968vw;
}
.bookImg {
  margin: 0.33266799733vw 2.66134397871vw 0.33266799733vw 2.66134397871vw;
}
img {
  width: 7.98403193613vw;
  height: 9.98003992016vw;
}
.bookName {
  width: 20.29vw;
  font-size: 1.06vw;
  margin: 0.66vw 0 0 2.328vw;
}
.bookBoxRight {
  width: 9.98003992016vw;
  margin: 0.66vw 2.66vw 0.332vw 2.66vw;
}
button {
  background-color: #20639b;
  color: #f8f8f8;
  border: none;
  width: 20px;
  text-align: center;
}
button:hover {
  cursor: pointer;
}
.orderAll {
  width: 15%;
  height: 10.97vw;
  box-shadow: 2px 5px 4px rgba(0, 0, 0, 0.25);
  border-radius: 0.3992015968vw;
  margin-top: 6vw;
  background-color: #20639b;
  color: #f8f8f8;
  padding: 1.996vw 0 0 6.653vw;
  position: fixed;
  right: 10vw;
}
#order {
  font-size: 1.197vw;
  display: inline-flex;
}
#iconCart {
  width: 1.99600798403vw;
  height: 1.99600798403vw;
  margin-left: 0.33266799733vw;
}
</style>
