<template>
  <div style="text-align: center;">
    <h2>รายการการจอง</h2>
    <table v-if="bookings.length > 0">
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
          <td scope="row">{{ booking.name }}</td>
          <td scope="row">{{ booking.email }}</td>
          <td scope="row">{{ booking.tel }}</td>
          <td scope="row">{{ booking.date }}</td>
          <td scope="row">{{ booking.time }}</td>
          <td scope="row">{{ booking.table }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const bookings = ref([]);

const tel = ref("");
const table = ref("");
const time = ref("");
const date = ref("");

const getTravelName = (itemName) => {
const travel = travellist.value.find((t) => t.name === itemName);
return travel ? travel.name : "";
};
</script>
