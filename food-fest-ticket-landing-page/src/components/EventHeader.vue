<script setup>
defineProps({
  count: Number
})
</script>

<template>
  <header class="header">
    <div>
      <h1>Food Fest 2026 </h1>
      <p>Experience the ultimate food and culture festival</p>
    </div>

    <div class="fav">
       Favourites: {{ count }}
    </div>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px;
  background: linear-gradient(135deg, #ff6b35, #ff8c42);
  color: white;
}

.header h1 {
  margin: 0;
}

.header p {
  margin: 5px 0 0;
  font-size: 14px;
}

.fav {
  background: rgba(255,255,255,0.2);
  padding: 10px 15px;
  border-radius: 20px;
}
</style>