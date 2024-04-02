<template>
  <div class="foodspots-view">
    <h1>Here you can see the foodspot list according to your taste!</h1>

    <div class="foodspots-table">
      <table>
        <thead>
        <tr>
          <th>Adresse</th>
          <th>Bewertung</th>
          <th>Kategorie</th>
          <th>Name</th>
          <th>Webseite</th>
          <th>Action</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="foodSpot in foodSpotsList" :key="foodSpot.id">
          <td>{{ foodSpot.address }}</td>
          <td>{{ foodSpot.rating }}</td>
          <td>{{ foodSpot.category }}</td>
          <td>{{ foodSpot.name }}</td>
          <td><a :href="foodSpot.website" target="_blank">Visit</a></td>
          <td>
            <div v-if="selectedFoodSpotId !== foodSpot.id">
              <button @click="showButtons(foodSpot.id)">Edit</button>
            </div>
            <div v-else>
              <button @click="confirm(foodSpot.id)"><i class="fas fa-check"></i></button>
              <button @click="deleteFoodSpot(foodSpot.id)"><i class="fas fa-trash"></i></button>
            </div>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>


  <create-food-spot-form @created="addFoodSpot"></create-food-spot-form>
</template>

<script>
import { toFormData } from "axios";
import CreateFoodSpotForm from "@/components/CreateFoodSpotForm.vue";

export default {
  name: "FoodSpotsView",
  components: {
    CreateFoodSpotForm,
  },
  data() {
    return {
      foodSpotsList: [],
      selectedFoodSpotId: null,
    };
  },
  methods: {
    toFormData,
    fetchFoodSpotsList() {
      const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + "/FoodSpotsList";
      const requestOptions = {
        method: "GET",
        redirect: "follow",
      };

      fetch(endpoint, requestOptions)
          .then((response) => response.json())
          .then((result) => {
            this.foodSpotsList = result;
          })
          .catch((error) => console.log("error", error));
    },
    showButtons(foodSpotId) {
      this.selectedFoodSpotId = foodSpotId;
    },
    confirm(foodSpotId) {
      console.log("Bestätigt:", foodSpotId);
      this.selectedFoodSpotId = null;
    },
      deleteFoodSpot(foodSpotId) {
          const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + "/FoodSpotsList/" + foodSpotId;
          const requestOptions = {
              method: "DELETE",
              redirect: "follow",
          };
          fetch(endpoint, requestOptions)
              .then((response) => {
                  if (response.ok) {
                      console.log("Gelöscht:", foodSpotId);
                      this.fetchFoodSpotsList();
                  } else {
                      console.log("Fehler beim Löschen des FoodSpots:", response.status);
                  }
              })
              .catch((error) => console.log("Fehler beim Löschen des FoodSpots:", error));
      },
    addFoodSpot() {
      const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + "/FoodSpotsList";
      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(/* Hinzufügen der Daten für den neuen FoodSpot */),
      };

      fetch(endpoint, requestOptions)
          .then((response) => response.json())
          .then((result) => {
            console.log("FoodSpot hinzugefügt:", result);
            this.fetchFoodSpotsList();
          })
          .catch((error) => console.log("Fehler beim Hinzufügen des FoodSpots:", error));
    },
  },
  mounted() {
    this.fetchFoodSpotsList();
  },
};
</script>

<style scoped>
.foodspots-view {
  text-align: center;
  margin-top: 20px;
}

.foodspots-table {
  margin: 0 auto;
  max-width: 800px;
}

table {
  border-collapse: collapse;
  width: 100%;
  length: 150%;
}

th,
td {
  border: 1px solid #ddd;
  padding: 8px;
}

th {
  background-color: #f2f2f2;
}

tr:nth-child(even) {
  background-color: #f9f9f9;
}

a {
  text-decoration: none;
  color: #007bff;
}

a:hover {
  text-decoration: underline;
}

i {
  cursor: pointer;
}

.fa-check {
  color: green;
}

.fa-trash {
  color: red;
}

.button-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.button-group {
  display: flex;
  gap: 5px;
}
</style>
