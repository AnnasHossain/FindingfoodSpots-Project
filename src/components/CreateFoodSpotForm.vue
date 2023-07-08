<template>
<button class="btn btn-success sticky-button" data-bs-toggle="offcanvas" data-bs-target="#foodspots-create-offcanvas" aria-controls="#foodspots-create-offcanvas">Toggle right offcanvas
<i class="bi bi-foodspots-plus-fill"></i>
</button>
<div class="offcanvas offcanvas-end" tabindex="-1" id="foodspots-create-offcanvas" aria-labelledby="offcanvasLabel">
<div class="offcanvas-header">
    <h5 id="offcanvas-label">New FoodSpot</h5>
    <button type="button" id="close-offcanvas" class="btn-close text-reset" data-bs-dismiss="offcanvas" aria-label="Close"></button>
</div>
<div class="offcanvas-body">
    <form class="text-start needs-validation" id="create-foodspot" novalidate>
        <div class="mb-3">
            <label for="name" class="form-label"> Name </label>
            <input type="text" class="form-control" id="name" v-model="Name" required>
            <div class="invalid feedback">
                Please provide the name of the restaurant.
            </div>
        </div>
        <div class="mb-3">
            <label for="category" class="form-label"> Kategorie </label>
            <input type="text" class="form-control" id="category" v-model="Kategorie" required>
            <div class="invalid-feedback">
                Please provide the category.
            </div>
        </div>
        <div class="mb-3">
            <label for="category" class="form-label">Kategorie</label>
            <select id="category" class="form-select" v-model="Kategorie" required>
                <option value="" selected disabled>Choose...</option>
                <option value="fast food">Male</option>
                <option value="asiatische Küche">Female</option>
                <option value="französische Küche">Diverse</option>
                <option value="japanische Küche">Diverse</option>
                <option value="französische Küche">Diverse</option>
            </select>
            <div class="invalid-feedback">
                Please select a valid gender.
            </div>
        </div>
        <div class="mb-3">
            <label for="last-name" class="form-label">Last name</label>
            <input type="text" class="form-control" id="last-name" v-model="lastName" required>
            <div class="invalid-feedback">
                Please provide the last name.
            </div>
        </div>
        <div class="mb-3">
            <label for="last-name" class="form-label">Last name</label>
            <input type="text" class="form-control" id="last-name" v-model="lastName" required>
            <div class="invalid-feedback">
                Please provide the last name.
            </div>
        </div>
        <div class="mb-3">
            <label for="last-name" class="form-label">Last name</label>
            <input type="text" class="form-control" id="last-name" v-model="lastName" required>
            <div class="invalid-feedback">
                Please provide the last name.
            </div>
        </div>
    </form>
    ...
</div>
</div>
</template>

<script>
/* export default un der ganze kram kommt hier rein */
</script>

<style scoped>
.sticky-button {
    position: fixed;
    bottom: 20px;
    right: 20px;
    padding: 10px 15px;
    border-radius: 30px;
}
</style>