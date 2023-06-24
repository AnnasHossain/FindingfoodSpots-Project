<template>
  <div class="FoodspotsView">
    <h1>Here you can see the foodspot list according to your taste! </h1>

<div class="col" v-for="FoodSpotsList in FoodSpotsList" :key="FoodSpotsList.id">


<table>
    <thead>
    <tr>
        <th>Adresse</th>
        <th>Bewertung</th>
        <th>Kategorie</th>
        <th>Name</th>
        <th></th>
    </tr>
    </thead>
    <tbody>

    <td>{{ FoodSpotsList.address }}</td>
    <td>{{ FoodSpotsList.rating }}</td>
    <td><a :href="FoodSpotsList.website" target="_blank">visit</a></td>
    <td>{{ FoodSpotsList.category }}</td>
    <td>{{ FoodSpotsList.name }}</td>

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


            FoodSpotsList: [],

            id: '',
            name: '',
            category: '',
            address: '',
            rating: '',
            website: ''

        }
    },
    mounted () {
        const endpoint = 'http://localhost:8080/FoodSpotsList'
        const requestOptions = {
         method: 'GET',
         redirect: 'follow'
        }
        fetch(endpoint, requestOptions)
            .then(response => response.json())
            .then(result => result.forEach(foodspot => {
                this.foodspots.push(foodspot)
            }))
            .catch(error => console.log('error', error))
    }
}

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
