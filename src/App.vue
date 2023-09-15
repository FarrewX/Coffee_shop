<script setup>
import Card from './components/Card.vue';
import { ref } from 'vue';

const bookings = ref([]);

const addReservation = (reservation) => {
  bookings.value.push(reservation);
};


const tel = ref("");
const table = ref("");
const time = ref("");
const date = ref("");

</script>

<template>
  <header></header>
  <h1 style="text-align: center;">ร้านอาหาร</h1>

  <div class="wrapper app">
    <Card :addReservation="addReservation" />
    <div style="text-align: center;">
    <h2>รายการการจอง</h2>
    <table v-if="bookings.length > 0" style="margin-left: 30%;">
      <thead>
        <tr>
          <th scope="col">ชื่อ: </th>
          <th scope="col">อีเมล: </th>
          <th scope="col">เบอร์ติดต่อ: </th>
          <th scope="col">วันที่: </th>
          <th scope="col">เวลา: </th>
          <th scope="col">จำนวนโต๊ะ: </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(booking, index) in bookings" :key="index">
          <td scope="row">&ensp;{{ booking.name }}&ensp;</td>
          <td scope="row">{{ booking.email }}&ensp;</td>
          <td scope="row">{{ booking.tel }}&ensp;</td>
          <td scope="row">{{ booking.date }}&ensp;</td>
          <td scope="row">{{ booking.time }}&ensp;</td>
          <td scope="row">{{ booking.table }}&ensp;</td>
        </tr>
      </tbody>
    </table>
  </div>
  </div>

  <footer></footer>
</template>
