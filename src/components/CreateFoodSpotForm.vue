<template>
    <button class="btn btn-primary sticky-button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight" aria-controls="offcanvasRight"><i class="bi bi-cup-straw"></i></button>

    <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
        <div class="offcanvas-header">
            <h5 class="offcanvas-title" id="offcanvasRightLabel">Add a new Foodspot!</h5>
            <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
        </div>
        <div class="offcanvas-body">
            <form class="text-start needs-validation" id="create-foodspot" novalidate>
                <div class="mb-3">
                    <label for="name" class="form-label"> Name </label>
                    <input type="text" class="form-control" id="name" v-model="name" required>
                    <div class="invalid feedback">
                        Please provide the name of the restaurant.
                    </div>
                </div>
                <div class="mb-3">
                    <label for="category" class="form-label">Kategorie</label>
                    <select id="category" class="form-select" v-model="category" required>
                        <option value="" selected disabled>Choose...</option>
                        <option value="fast food">fast food</option>
                        <option value="asiatische Küche">asiatische Küche</option>
                        <option value="französische Küche">französische Küche</option>
                        <option value="japanische Küche">japanische Küche</option>
                        <option value="orientalische Küche">orientalische Küche</option>
                    </select>
                    <div class="invalid-feedback">
                        Please select a valid category.
                    </div>
                </div>
                <div class="mb-3">
                    <label for="address" class="form-label">Adresse</label>
                    <input type="text" class="form-control" id="address" v-model="address" required>
                    <div class="invalid-feedback">
                        Please provide the address.
                    </div>
                </div>
                <div class="mb-3">
                    <label for="website" class="form-label">Webseite</label>
                    <input type="text" class="form-control" id="website" v-model="website" required>
                    <div class="invalid-feedback">
                        Please provide the hyperlink of the website.
                    </div>
                </div>
                <div class="mb-3">
                    <label for="rating" class="form-label">Bewertung</label>
                    <input type="text" class="form-control" id="rating" v-model="rating" required>
                    <div class="invalid-feedback">
                        Please provide the rating.
                    </div>
                </div>
                <div class="mt-5">
                    <button type="submit" class="btn btn-primary" @click.prevent="createFoodSpot"> Create</button>
                    <button type="reset" class="btn btn-danger" >Reset</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {

    name: 'CreateFoodSpotForm',
    data(){
        return {
            name: '',
            address: '',
            rating: '',
            category:'',
            website:'',
            serverValidationMessage: []
        }
    },
    emits: ['created'],
    methods: {
        async createFoodSpot () {
            if (this.validate()) {
                const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/FoodSpotsList'

                const headers = new Headers()
                headers.append('Content-Type', 'application/json')

                const FoodSpot = JSON.stringify({
                    name: this.name,
                    address: this.address,
                    rating: this.rating,
                    category: this.category,
                    website: this.website
                })
                const requestOptions = {
                    method: 'POST',
                    headers: headers,
                    body: FoodSpot,
                    redirect: 'follow'
                }
                const response = await fetch(endpoint, requestOptions)
              // Ergänzung;         || Denn weiter oben habe ich emits: ... gemacht was aber nicht reicht um das event auszulösen, deshalb noch diese Zeilen
                const result = await response.json()
                this.$emit('created', result)
            }
        },
        validate () {
            //const form = document.getElementById('create-food-spot-form')// stimmt nicht überein mit dem was im template steht
            const form = document.getElementById('create-foodspot') // Wenn immernoch Fehler, dann Formular anpassen mit dem was ich darüber hab
            // WEITERER FEHLER: in einer anderen Datei (FoodspotsView) hatte ich auch eine add Funktion, was keinen Sinn macht, weil die add Funktion in dieser Datei gemacht wird
            form.classList.add('was-validated')
            return form.checkValidity()
        }
    }
}
</script>

<style scoped>
.sticky-button {
    position: fixed;
    bottom: 20px;
    right: 20px;
    padding: 10px 15px;
    border-radius: 30px;
}
.btn-primary.sticky-button::after {
  content: '+'; /* Insert "+" symbol as content */
  position: absolute; /* Position the symbol absolutely */
  bottom: 0; /* Set bottom to 0 for bottom edge placement */
  right: 10px; /* Set right to 0 for right edge placement */
  font-size: 20px; /* Adjust the symbol size as desired */
  color: white; /* Set the symbol color */
}


</style>
<script setup>
</script>
