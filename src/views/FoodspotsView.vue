<template>
  <div class="FoodspotsView">
    <h1>Here you can see the foodspot list according to your taste!</h1>

    <div class="col">
      <table class="table">
        <thead>
        <tr>
          <th scope="col">Adresse</th>
          <th scope="col">Bewertung</th>
          <th scope="col">Kategorie</th>
          <th scope="col">Name</th>
          <th scope="col">Webseite</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="foodSpot in FoodSpotsList" :key="foodSpot.id">
          <td>{{ foodSpot.address }}</td>
          <td>{{ foodSpot.rating }}</td>
          <td><a :href="foodSpot.website" target="_blank">visit</a></td>
          <td>{{ foodSpot.category }}</td>
          <td>{{ foodSpot.name }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FoodSpotList',
  data() {
    return {
      FoodSpotsList: []
    }
  },
  methods: {
    addFoodSpot (foodSpotLocation) {
      const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + foodSpotLocation
      const requestOptions = {
        method: 'GET',
        redirect: 'follow'
      }

      fetch(endpoint, requestOptions)
          .then(response => response.json())
          .then(foodSpot => this.FoodSpotsList.push(foodSpot))
          .catch(error => console.log('error', error))
    }
  },
  mounted() {
    //const endpoint = ;
    const requestOptions = {
      method : 'GET',
      redirect : 'follow'
    }

    fetch('http://localhost:3000/FoodSpotsList', requestOptions)
        .then(response => response.json())
        .then(result => result.forEach(foodSpot => {
          this.FoodSpotsList.push(foodSpot)
          this.FoodSpotsList = JSON.parse(foodSpot);
        }))

        .catch(error => {
          console.log('Error', error);
        });
  }
};
</script>

<style>
table {
  border-collapse: collapse;
}

table, th, td {
  border: 1px solid black;
}

th, td {
  padding: 5px;
}

.col {
  margin-left: auto;
  margin-right: auto;
  max-width: 380px;
}
</style>