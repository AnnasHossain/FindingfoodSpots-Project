<template>
    <div class="about">
        <h1>This is an about page</h1>
        <input type="text" v-model="name" placeholder="Enter username" />
        <button type="button" class="btn btn-primary active" @click="login">Login</button>
        <p v-if="showErrorMessage" class="error-message">Der Benutzer ist nicht vorhanden. Bitte registrieren.</p>
    </div>
</template>
<script>export default {
    data() {
        return {
            name: "",
            showErrorMessage: false,
        };
    },
    methods: {
        login() {
            fetch("http://localhost:8080/Nutzers")
                .then(response => response.json())
                .then(Nutzer => {
                    const foundNutzer = Nutzer.find(Nutzers => Nutzers.name === this.name);

                    if (foundNutzer) {
                        console.log("Benutzer erfolgreich eingeloggt");
                        this.$router.push("/foodspots");
                    } else {
                        this.showErrorMessage = true;
                        console.log("Der Benutzer ist nicht vorhanden. Bitte registrieren.");
                    }
                })
                .catch(error => {
                    console.error("Fehler beim Abrufen der Benutzerdaten:", error);
                });
        },
    },
};
</script>
<style>
.error-message {
    color: red;
    font-weight: bold;
}
</style>