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
          <td>{{ FoodSpotsList.address }}</td>
          <td>{{ FoodSpotsList.rating }}</td>
          <td>{{ FoodSpotsList.category }}</td>
          <td>{{ FoodSpotsList.name }}</td>
            <td><a :href="FoodSpotsList.website" target="_blank">visit</a></td>
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
  },  methods: {
        addFoodspot (FoodSpotsLocation) {
            const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + FoodSpotsLocation
            const requestOptions = {
                method: 'GET',
                redirect: 'follow'
            }

            fetch(endpoint, requestOptions)
                .then(response => response.json())
                .then(foodspot => this.FoodSpotsList.push(foodspot))
                .catch(error => console.log('error', error))
        }
    },
  mounted() {
    //const endpoint = ;
   const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/FoodSpotList'
   console.log("Working Backend?")
    const requestOptions = {
      method : 'GET',
      redirect : 'follow'
    }

    fetch(endpoint, requestOptions)
        .then(response => response.json())
        .then(result => console.log(result))
        .catch(error => console.log('error', error))

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