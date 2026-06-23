<script setup>
const props = defineProps({
  ticket: Object
})

const emit = defineEmits(['favourite'])

function favouriteTicket() {
  emit('favourite')
}
</script>

<template>
  <div class="card" :class="{ featured: ticket.featured }">

    <div v-if="ticket.featured" class="ribbon">
      FEATURED
    </div>

    <h2>{{ ticket.name }}</h2>

    <p class="price">R{{ ticket.price }}</p>

    <p v-if="ticket.featured" class="badge">
       Featured Ticket
    </p>

    <ul>
      <li v-for="item in ticket.benefits" :key="item">
        {{ item }}
      </li>
    </ul>

    <button
    @click="favouriteTicket"
    :disabled="ticket.favourited"
    >
    {{ ticket.favourited ? ' Favourited' : ' Favourite' }}
    </button>

  </div>
</template>

<style scoped>
.card {
  background: white;
  position: relative;
  color: #333;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  transition: 0.3s;
}

.ribbon {
  position: absolute;
  top: 10px;
  right: -10px;
  background: #ff6b35;
  color: white;
  padding: 5px 10px;
  font-size: 12px;
  transform: rotate(10deg);
  border-radius: 5px;
}

.card:hover {
  transform: translateY(-5px);
}

.price {
  font-size: 20px;
  font-weight: bold;
  margin: 10px 0;
}

.badge {
  background: gold;
  padding: 5px 10px;
  display: inline-block;
  border-radius: 10px;
  font-size: 12px;
  margin-bottom: 10px;
}

.featured {
  border: 2px solid #ffd700;
  background: linear-gradient(135deg, #fff8dc, #ffffff);
  transform: scale(1.05);
  position: relative;
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}

ul {
  padding-left: 18px;
}

button {
  margin-top: 10px;
  width: 100%;
  padding: 10px;
  border: none;
  background: #ff6b35;
  color: white;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background: #e85a2a;
}

button:disabled {
  background: #999;
  cursor: not-allowed;
}
</style>