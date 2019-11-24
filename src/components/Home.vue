<template>
  <div  id="home" class="font-kanit">
    <div>
      <img class="responsive-img" v-bind:src="'/static/home/main.jpg'" >
    </div>

    <div class="rec-home-2">
      <h3 class="text-topic-2">ค้นหา ติดต่อเจ้าของหอพัก ย้ายเข้าอยู่ได้ทันที</h3>
      <img class="icon-magnifier" v-bind:src="'/static/home/magnifier.jpg'" >
      <img class="icon-left-arrow-1" v-bind:src="'/static/home/left-arrow.jpg'" >
      <img class="icon-call" v-bind:src="'/static/home/call.jpg'" >
      <img class="icon-left-arrow-2" v-bind:src="'/static/home/left-arrow.jpg'" >
      <img class="icon-bed" v-bind:src="'/static/home/bed.jpg'" >
      <h4 class="text-h4 text-detail-method-1">ค้นหาห้องที่ใช้และตรงความต้องการของคุณ</h4>
      <h4 class="text-h4 text-detail-method-2">ติดต่อเจ้าของหอพักเพื่อดูห้องและทำสัญญา</h4>
      <h4 class="text-h4 text-detail-method-3">ย้ายเข้าห้องพักใหม่เปรียบเสมือนเป็นบ้านของตัวเอง</h4>
    </div>

    <div class="rec-home-3">
      <a class="line-home-1"></a>
      <h1 class="text-topic-3">หอพักแนะนำ</h1>
      <h4 class="text-h4 text-topic-3-detail">ค้นหา หอพัก อพาร์ทเม้นท์ ยอดนิยม</h4>
    </div>

    <div class="rec-home-4">

      <h1 class="text-ap-home text-name-ap-home-1">บ้านหมอกเมฆ</h1>
      <img class="ap-1" v-bind:src="'/static/home/ap-1.jpg'">
      <h4 class="text-h4 text-detail-ap-1">บ้านหมอกเมฆ ห้องใหญ่มาก ฟรี Wifi&Fitness ห้องใหญ่มาก
        บนถนนรัชดาฯ ใกล้ MRT ห้วยขวาง ฟรี Wifi & Fitness
        Apartment สไตล์โมเดิร์น เพียง 10 นาทีจาก MRT ห้วยขวาง
      </h4>
      <button type="submit" class="button button-ap-home-1"><h4 class="text-h4 text-button-ap-home">More Info</h4></button>


      <h1 class="text-ap-home text-name-ap-home-2">ศิริเพลส อพาร์ทเม้นท์</h1>
      <img class="ap-2" v-bind:src="'/static/home/ap-2.jpg'">
      <h4 class="text-h4 text-detail-ap-2">ห้องพักสะอาด กว้างขวาง สะดวกสบาย มีขนาดให้เลือกหลายแบบ มีที่จอดรถ
        ใกล้โรงพยาบาลสินแพทย์ ใกล้สี่แยกศรีอุดม เงียบสงบ เฟอร์นิเจอร์ครบ ห้องกว้างกว่า ใหม่ สะอาด มีรปภ.ดูแล บริการซักรีด
      </h4>
      <button type="submit" class="button button-ap-home-2"><h4 class="text-h4 text-button-ap-home">More Info</h4></button>


      <h1 class="text-ap-home text-name-ap-home-3">บ้านเมฆหมอก</h1>
      <img class="ap-3" v-bind:src="'/static/home/ap-1.jpg'">
      <h4 class="text-h4 text-detail-ap-3">บ้านเมฆหมอก ห้องเล็กมาก Wifi & Fitness เสียเงินเพิ่ม
        บนถนนรัชดาฯ ใกล้ BTS ห้วยขวาง
        Apartment สไตล์โมเดิร์น เพียง 10 นาทีจาก BTS ห้วยขวาง
      </h4>
      <button type="submit" class="button button-ap-home-3"><h4 class="text-h4 text-button-ap-home">More Info</h4></button>

    </div>

    <div class="rec-home-7">
      <a class="line-home-3"></a>

      <h4 class="text-h4 text-topic-how-to-home-2">วิธีการชำระเงิน</h4>
      <a href="#">
        <img v-bind:src="'/static/home/bangkok-bank.png'" class="logo-bangkok-bank">
      </a>
      <a href="#">
        <img v-bind:src="'/static/home/kasikorn-bank.png'" class="logo-kasikorn-bank">
      </a>
        <img v-bind:src="'/static/home/krungsri-bank.png'" class="logo-krungsri-bank">
      </a>
      <a href="#">
        <img v-bind:src="'/static/home/krungthai-bank.jpg'"class="logo-krungthai-bank">
      </a>
      <a href="#">
        <img v-bind:src="'/static/home/paypal.png'" class="logo-paypal">
      </a>
      <a href="#">
        <img v-bind:src="'/static/home/scb-bank.png'" class="logo-scb-bank">
      </a>

    </div>

  </div>
</template>

<script>

</script>

<style>
.font-kanit {
  font-family: 'Kanit', sans-serif;
}

.button  {
  background-color: #FFFFFF;
  border-radius: 5px;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;

  cursor: cursor;
}

.rec-home-1 {
  width: 100%;
  height: 400px;
}

.rec-home-2 {
  height: 262px;
  width: 100%;
  background: #FFFFFF;
}

.rec-home-3 {
  height: 250px;
  width: 100%;
  background: #FFFFFF;
}

.rec-home-4 {
  height: 600px;
  width: 100%;
  background: #F1F1F1;
}

.rec-home-7 {
  height: 400px;
  width: 100%;
  background: #FFFFFF;
}

.text-topic-search {
  position: absolute;
  top: 250px;
  left: 370px;

  font-style: normal;
  font-weight: bold;
  font-size: 45px;
  line-height: 12px;
  color: #FFFFFF;
}

.text-topic-2 {
  position: absolute;
  color: #00BFFF;
  font-style: normal;
  line-height: 60px;
  top: 700px;
  left: 600px;
}

.icon-magnifier {
  position: absolute;
  width: 120px;
  height: 120px;
  top: 800px;
  left: 570px;
}

.icon-left-arrow-1 {
  position: absolute;
  width: 72px;
  height: 72px;
  top: 800px;
  left: 770px;
}

.icon-left-arrow-2 {
  position: absolute;
  width: 72px;
  height: 72px;
  top: 800px;
  left: 1110px;
}

.icon-call {
  position: absolute;
  width: 120px;
  height: 120px;
  top: 800px;
  left: 910px;
}

.icon-bed {
  position: absolute;
  width: 120px;
  height: 120px;
  top: 800px;
  left: 1265px;
}

.text-detail-method-1 {
  position: absolute;
  text-align: center;
  line-height: 17px;
  width: 150px;
  top: 930px;
  left: 550px;
  color: #00BFFF;
}

.text-detail-method-2 {
  position: absolute;
  text-align: center;
  line-height: 17px;
  width: 150px;
  top: 930px;
  left: 900px;
  color: #00BFFF;
}

.text-detail-method-3 {
  position: absolute;
  text-align: center;
  line-height: 17px;
  width: 150px;
  top: 930px;
  left: 1250px;
  color: #00BFFF;
}

.text-h4 {
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 14px;
}

.line-home-1 {
  position: absolute;
  left: 15.55%;
  right: 12.58%;
  top: 1050px;
  bottom: 75.81%;

  border: 0.8px solid #707070;
}

.text-topic-3 {
  position: absolute;
  color: #00BFFF;
  font-style: normal;
  font-size: 25px;
  line-height: 48px;
  top: 1050px;
  left: 920px;
}

.text-topic-3-detail {
  position: absolute;
  color: #58595B;
  font-style: normal;
  line-height: 38px;
  top: 1110px;
  left: 870px;
}

.text-ap-home {
  font-style: normal;
  font-size: 25px;
  line-height: 12px;
  color: #58595B;
}

.text-name-ap-home-1 {
  position: absolute;
  color: black;
  top: 1250px;
  left: 300px;
}

.text-name-ap-home-2 {
  position: absolute;
  color: black;
  top: 1250px;
  left: 800px;
}

.text-name-ap-home-3 {
  position: absolute;
  color: black;
  top: 1250px;
  left: 1300px;
}

.ap-1 {
  position: absolute;
  width: 340px;
  height: 220px;
  top: 1330px;
  left: 300px;
}

.ap-2 {
  position: absolute;
  width: 340px;
  height: 220px;
  top: 1330px;
  left: 800px;
}

.ap-3 {
  position: absolute;
  width: 340px;
  height: 220px;
  top: 1330px;
  left: 1300px;
}

.button-ap-home-1 {
  position: absolute;
  width: auto;
  height: 35px;
  left: 300px;
  top: 1670px;
  border: 2px solid #00BFFF;
}

.button-ap-home-2 {
  position: absolute;
  width: auto;
  height: 35px;
  left: 800px;
  top: 1670px;
  border: 2px solid #00BFFF;
}

.button-ap-home-3 {
  position: absolute;
  width: auto;
  height: 35px;
  left: 1300px;
  top: 1670px;
  border: 2px solid #00BFFF;
}


.text-detail-ap-1 {
  position: absolute;
  color: black;
  width: 340px;
  line-height: 18px;
  top: 1550px;
  left: 300px;
  color: #58595B;
}

.text-detail-ap-2 {
  position: absolute;
  color: black;
  width: 340px;
  line-height: 18px;
  top: 1550px;
  left: 800px;
  color: #58595B;
}

.text-detail-ap-3 {
  position: absolute;
  color: black;
  width: 340px;
  line-height: 18px;
  top: 1550px;
  left: 1300px;
  color: #58595B;
}

.text-button-ap-home {
  position: relative;
  font-size: 16px;
  line-height: 5px;
  left: 0px;
  top: -25px;
  color: black;
}

.line-home-3 {
  position: absolute;
  width: 100%;
  top: 1900px;

  border: 1.5px solid #707070;
}

.text-topic-how-to-home-2 {
  position: absolute;
  font-weight: bold;
  top: 1930px;
  left: 900px;
  color: #58595B;
}

.logo-bangkok-bank {
  position: absolute;
  top: 2000px;
  left: 625px;
  width: 140px;
  height: 48px;
  border: 1px solid #58595B;
}

.logo-kasikorn-bank {
  position: absolute;
  top: 2000px;
  left: 795px;
  width: 140px;
  height: 48px;
  border: 1px solid #58595B;
}

.logo-krungsri-bank {
  position: absolute;
  top: 2000px;
  left: 965px;
  width: 140px;
  height: 48px;
  border: 1px solid #58595B;
}

.logo-krungthai-bank {
  position: absolute;
  top: 2000px;
  left: 1135px;
  width: 140px;
  height: 48px;
  border: 1px solid #58595B;
}

.logo-paypal {
  position: absolute;
  top: 2070px;
  left: 795px;
  width: 140px;
  height: 48px;
  border: 1px solid #58595B;
}

.logo-scb-bank {
  position: absolute;
  top: 2070px;
  left: 965px;
  width: 140px;
  height: 48px;
  border: 1px solid #58595B;
}


</style>
