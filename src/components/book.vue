<template>
  <div class="book">
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
          <input type="number" />
          เล่ม
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "book",
  props: {
    bookData: Object
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
