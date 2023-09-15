<script setup>
import Card from './components/Card.vue';
import Reservation from './components/Reservation.vue';
import { ref } from 'vue';

const bookings = ref([]);

const addReservation = (reservation) => {
  bookings.value.push(reservation);
};
</script>

<template>
  <header></header>
  <h1 style="text-align: center;">ร้านกาแฟ</h1>

  <div class="wrapper app" style="align-items: center;">
    <Card :addReservation="addReservation" />
    <Reservation :bookings="bookings" />
  </div>

  <footer></footer>
</template>
