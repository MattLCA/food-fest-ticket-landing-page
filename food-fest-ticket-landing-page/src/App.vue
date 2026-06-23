<script setup>
import { ref } from 'vue'
import EventHeader from './components/EventHeader.vue'
import TicketCard from './components/TicketCard.vue'

const favouriteCount = ref(0)

function addFavourite(ticket) {
  if (!ticket.favourited) {
    ticket.favourited = true
    favouriteCount.value++
  }
}

const tickets = ref([
  {
    id: 1,
    name: 'Golden Pass',
    price: 499,
    featured: true,
    favourited: false,
    benefits: ['Front row access', 'Free drinks', 'Meet chefs']
  },
  {
    id: 2,
    name: 'Silver Pass',
    price: 299,
    featured: false,
    favourited: false,
    benefits: ['General entry', 'Food stalls access']
  },
  {
    id: 3,
    name: 'Bronze Pass',
    price: 149,
    featured: false,
    favourited: false,
    benefits: ['Entry only']
  }
])
</script>

<template>
  <EventHeader :count="favouriteCount" />

  <div class="container">
    <TicketCard
      v-for="ticket in tickets"
      :key="ticket.id"
      :ticket="ticket"
      @favourite="addFavourite(ticket)"
    />
  </div>
</template>

<style>
body {
  margin: 0;
  font-family: Arial;
  background: #f4f4f4;
}

.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  padding: 20px;
}
</style>
