<script setup>
import { defineProps, ref } from 'vue';

const { addReservation } = defineProps(['addReservation']);
const addReservationRef = ref(addReservation);

const isFormVisible = ref(false);
const formData = ref({
  name: '',
  email: '',
  tel: '',
  date: '',
  time: '',
  table: ''

});

const showForm = (index) => {
  // กำหนดข้อมูลเริ่มต้นให้กับแบบฟอร์ม
  formData.value = {
    name: '',
    email: '',
    tel: '',
    date: '',
    time: '',
    table: ''
  };
  isFormVisible.value = true;
};

const hideForm = () => {
  isFormVisible.value = false;
};

const submitForm = () => {
  // เก็บข้อมูลการจอง
  const bookingData = {
    name: formData.value.name,
    email: formData.value.email,
    tel: formData.value.tel,
    date: formData.value.date,
    time: formData.value.time,
    table: formData.value.table
    // เพิ่มข้อมูล
  };
  // นำข้อมูลการจองไปเก็บ
  addReservation(bookingData);

  // หลังจากเก็บก็ซ่อนไว้
  hideForm();
};
</script>

<template>
    <div id="app contanier">
      <div class="card container" v-for="(item, index) in items" :key="index">
        <img :src="item.imageUrl" @click="showForm(index)">
        <p style="font-size: 20px;">ร้าน {{ item.title }}</p>
      </div>
      <div class="popup" v-if="isFormVisible">
      <div class="popup-content">   
        
        <form @submit.prevent="submitForm">
          <label>จองโต๊ะ</label>
          <label for="name">ชื่อ:</label>
          <input type="text" id="name" v-model="formData.name" required>

          <label for="email">อีเมล:</label>
          <input type="email" id="email" v-model="formData.email" required>

          <label for="tel">เบอร์ติดต่อ:</label>
          <input type="text" id="tel" v-model="formData.tel" required>

          <label for="date">วันที่:</label>
          <input type="date" id="date" v-model="formData.date" required>

          <label for="time">เวลา:</label>
          <input type="time" id="time" v-model="formData.time" required>

          <label for="table">จำนวนโต๊ะ:</label>
          <input type="number" min="1" id="table" v-model="formData.table" required>

          <button type="submit">ยืนยัน</button>
          <button class="buttonc" @click="hideForm">ยกเลิก</button>
        </form>
      </div>
    </div>
  </div>
   
</template>

<script>
import { ref } from "vue";

const items = ref([
  {
    title: 'ต๋องเต็มโต๊ะ',
    name: '',
    imageUrl: '../src/components/image/tonk.jpg',
    additionalInfo: 'ข้อมูลเพิ่มเติมสำหรับท่าช้าง'
  },
  {
    title: 'ข้าวซอยแม่สาย',
    name: '',
    imageUrl: '../src/components/image/maa.jpg',
    additionalInfo: 'ข้อมูลเพิ่มเติมสำหรับท่าช้าง'
  },
  {
    title: 'Papa Curry',
    name: '',
    imageUrl: '../src/components/image/papa.jpg',
    additionalInfo: 'ข้อมูลเพิ่มเติมสำหรับท่าช้าง'
  },
  {
    title: 'ครัวอาจารย์สายหยุด',
    name: '',
    imageUrl: '../src/components/image/sai.jpg',
    additionalInfo: 'ข้อมูลเพิ่มเติมสำหรับท่าช้าง'
  },
  {
    title: 'คั่วไก่นิมมาน',
    name: '',
    imageUrl: '../src/components/image/nim.jpg',
    additionalInfo: 'ข้อมูลเพิ่มเติมสำหรับท่าช้าง'
  },
]);


</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
}

img{
  width: 260px;
  height: 200px;
}
.card {
  width: 260px;
  margin: 5px;
  margin-right: 30px;
  margin-top: 40px;
  padding: auto;
  display: inline-block;
  cursor: pointer;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 10px;
  text-align: center;
}
.card-container {
  position:fixed;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: 20px;
}

.popup {
  display: none;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup-content {
  background-color: white;
  padding: 20px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  text-align: center;
}


form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

label {
  font-weight: bold;
}

input {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  padding: 5px 15px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.buttonc {
  padding: 5px 15px;
  background-color: #d50202;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}


button:hover {
  background-color: #0056b3;
}
</style>