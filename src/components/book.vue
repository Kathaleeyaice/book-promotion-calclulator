<template>
  <div class="book">
    <div class="bookBox">
      <div class="bookImg"></div>
      <div class="bookName">
        แฮรี่ พอตเตอร์กับศิลาอาถรรพ์
      </div>
      <div class="bookBoxRight">
        <div class="bookPrice">
          ราคา
        </div>
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
  props: {}
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
  width: 120px;
  height: 150px;
  background-color: antiquewhite;
  margin: 5px 35px 5px 35px;
}
.bookName {
  margin: 5px 35px 5px 35px;
}
.bookBoxRight {
  margin: 5px 35px 5px 35px;
}
</style>
