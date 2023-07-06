<template>
  <div class="home">
    <div class="banner">
      <h1 class="title">Willkommen bei FoodSpot</h1>
      <p class="subtitle">Entdecken Sie die besten Restaurants und Spezialitäten in Ihrer Nähe</p>
    </div>
    <div class="image-collage">
      <div class="image-wrapper dessert-wrapper">
        <router-link to="/about">
          <img class="image" src="../assets/dessertfoodspot.png" alt="Dessert-Foodspot">
        </router-link>
      </div>
      <div class="image-wrapper focus-wrapper">
        <router-link to="/about">
          <div class="image-zoom">
            <img class="image focus" src="../assets/döner.png" alt="Döner-Foodspot">
          </div>
        </router-link>
      </div>
      <div class="image-wrapper restaurant-wrapper">
        <router-link to="/about">
          <img class="image" src="../assets/restaurantpicture.png" alt="Restaurant-Foodspot">
        </router-link>
      </div>
    </div>
    <p class="image-collage-description">Entdecken Sie unsere vielfältige Auswahl an Foodspots!</p>
  </div>
</template>


<style scoped>
.home {
    text-align: center;
    background-color: #f5f5f5;
    padding: 2rem;
    height: 70vh;
}

.image-collage {
    display: flex;
    justify-content: center;
    gap: 2rem;
    margin-bottom: 2rem;
}

.image-wrapper {
    flex: 1;
    overflow: hidden;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.dessert-wrapper {
    margin-right: 1rem;
}

.restaurant-wrapper {
    margin-left: 1rem;
}

.focus-wrapper {
    position: relative;
}

.image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
}

.image:hover {
    transform: scale(1.1);
}

.focus {
    position: absolute;
    left: -10%;
    width: 120%;
    height: 100%;
    object-fit: cover;
    transform-origin: left;
    transition: transform 0.3s ease;
}

.banner {
    background-color: #f8f8f8;
    padding: 1rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 1rem;
}

.title {
    font-size: 2.5rem;
    color: #333;
    margin-bottom: 1rem;
}

.subtitle {
    font-size: 1.2rem;
    color: #666;
    margin-bottom: 1.5rem;
}

.cta-button {
    background-color: #ff7f50;
    color: #fff;
    padding: 0.8rem 2rem;
    font-size: 1.2rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.cta-button:hover {
    background-color: #ff6347;

}
</style>
<script setup>
</script>