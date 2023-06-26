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
                </tr>
                </thead>
                <tbody>
                <tr v-for="foodSpot in foodSpotsList" :key="foodSpot.id">
                    <td>{{ foodSpot.address }}</td>
                    <td>{{ foodSpot.rating }}</td>
                    <td>{{ foodSpot.category }}</td>
                    <td>{{ foodSpot.name }}</td>
                    <td><a :href="foodSpot.website" target="_blank">Visit</a></td>
                </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FoodSpotsView',
    data() {
        return {
            foodSpotsList: []
        }
    },
    methods: {
        fetchFoodSpotsList() {
            const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/FoodSpotsList'
            const requestOptions = {
                method: 'GET',
                redirect: 'follow'
            }

            fetch(endpoint, requestOptions)
                .then(response => response.json())
                .then(result => {
                    this.foodSpotsList = result
                })
                .catch(error => console.log('error', error))
        }
    },
    mounted() {
        this.fetchFoodSpotsList()
    }
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
}

th, td {
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
</style>
