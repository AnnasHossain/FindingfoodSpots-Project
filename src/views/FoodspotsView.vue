<template>
  <div class="FoodspotsView">
    <h1>Here you can see the foodspot list according to your taste! </h1>

<div class="col" v-for="foodspot in foodspots" :key="foodspot.id">


<table>
    <thead>
    <tr>
        <th>Lokalname</th>
        <th>Kategorie</th>
        <th>Adresse</th>
        <th>Bewertung</th>
        <th></th>
    </tr>
    </thead>
    <tbody>
    <td>{{ foodspot.name }}</td>
    <td>{{ foodspot.category }}</td>
    <td>{{ foodspot.address }}</td>
    <td>{{ foodspot.rating }}</td>
    <td><a :href="foodspot.website" target="_blank">visit</a></td>

    </tbody>
</table>

</div>
</div>
</template>

<script>
export default {
    data() {
        return {
            foodspots: [
                {
                    id: 1,
                    name: 'CITY CHICKEN BERLIN',
                    category: "fast food",
                    address: "Sonnenallee 59, 12045 Berlin",
                    rating: 5 + "/" + 5,
                    website: "https://www.city-chicken-berlin.de/"
                },
                {
                    id: 2,
                    name: "Lokalname 2",
                    category: "Kategorie 2",
                    address: "Adresse 2",
                    rating: 4 + "/" + 5,
                    website: "https://example.com/foodspot2"
                },
                {
                    id: 3,
                    name: "Lokalname 3",
                    category: "Kategorie 3",
                    address: "Adresse 3",
                    rating: 4 + "/" + 5,
                    website: "https://example.com/foodspot3"
                },
                // Füge hier weitere Foodspots hinzu...
            ]
        };
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
