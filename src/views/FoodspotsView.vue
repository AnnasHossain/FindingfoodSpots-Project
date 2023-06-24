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
                <tr v-for="foodSpot in foodSpotsList" :key="foodSpot.id">
                    <td>{{ foodSpot.address }}</td>
                    <td>{{ foodSpot.rating }}</td>
                    <td>{{ foodSpot.category }}</td>
                    <td>{{ foodSpot.name }}</td>
                    <td><a :href="foodSpot.website" target="_blank">visit</a></td>
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
            foodSpotsList: []
        };
    },
    mounted() {
        const endpoint = 'http://localhost:8080/FoodSpotsList';
        fetch(endpoint)
            .then(response => response.json())
            .then(data => {
                this.foodSpotsList = data;
            })
            .catch(error => {
                console.log('Error fetching data:', error);
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
</style>
