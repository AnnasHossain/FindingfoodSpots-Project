<template>
  <div class="about">
    <h1>This is an about page</h1>

<a href="http://localhost:3000/" target="_blank">
  <button type="button" class="btn btn-primary active" data-bs-toggle="button" aria-pressed="true">Finding Foodspots</button>
</a>
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
                    rating: "Bewertung 1",
                    website: "https://example.com/foodspot1"
                },
                {
                    id: 2,
                    name: "Lokalname 2",
                    category: "Kategorie 2",
                    address: "Adresse 2",
                    rating: "Bewertung 2",
                    website: "https://example.com/foodspot2"
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