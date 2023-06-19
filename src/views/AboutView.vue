<template>
  <div class="about">

    <h1>This is an about page</h1>

<a href="http://localhost:3000/" target="_blank">
  <button type="button" class="btn btn-primary active" data-bs-toggle="button" aria-pressed="true">Finding Foodspots</button>
</a>

      <h2>Foodspots in Berlin</h2>

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
              <td><a :href="foodspot.website" target="_blank">Besuchen</a></td>

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
                    name: 'Lokalname 1',
                    category: "Kategorie 1",
                    address: "Adresse 1",
                    rating: 3,
                    website: "https://example.com/foodspot1"
                },
                {
                    id: 2,
                    name: "Lokalname 2",
                    category: "Kategorie 2",
                    address: "Adresse 2",
                    rating: 4,
                    website: "https://example.com/foodspot2"
                },
                {
                    id: 3,
                    name: "Lokalname 3",
                    category: "Kategorie 3",
                    address: "Adresse 3",
                    rating: 4,
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