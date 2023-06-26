<template>
    <div class="about">
        <div class="content">
            <h1 class="title">About Us</h1>
            <p>Welcome to our company website. Learn more about who we are and what we do.</p>
        </div>
        <div class="login-form">
            <h2 class="login-title">Log In to Our Website</h2>
            <div class="input-group">
                <input type="text" v-model="name" class="login-input" placeholder="Name eingeben" />
            </div>
            <button type="button" class="login-btn" @click="login">Log In</button>
            <p v-if="showErrorMessage" class="error-message">The user does not exist. Please register.</p>
            <hr class="divider" />
            <button type="button" class="create-nutzer-btn">Create New User</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            showErrorMessage: false,
        };
    },
    methods: {
        login() {
            fetch("http://localhost:8080/Nutzers")
                .then((response) => response.json())
                .then((Nutzer) => {
                    const foundNutzer = Nutzer.find((Nutzers) => Nutzers.name === this.name);

                    if (foundNutzer) {
                        console.log("User logged in successfully");
                        this.$router.push("/foodspots");
                    } else {
                        this.showErrorMessage = true;
                        console.log("The user does not exist. Please register.");
                    }
                })
                .catch((error) => {
                    console.error("Failed to retrieve user data:", error);
                });
        },
    },
};
</script>

<style scoped>
.about {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f2f5;
}

.content {
    text-align: center;
    margin-right: 30px;
}

.title {
    font-size: 28px;
    font-weight: bold;
    margin-bottom: 20px;
}

.login-form {
    background-color: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.login-title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 16px;
}

.input-group {
    margin-bottom: 16px;
}

.login-input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
}

.login-btn {
    width: 100%;
    padding: 10px;
    background-color: #1877f2;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
}

.error-message {
    color: red;
    font-size: 14px;
    margin-top: 16px;
}

.forgot-password {
    font-size: 14px;
    text-decoration: none;
    color: #1877f2;
}

.divider {
    margin: 16px 0;
    border: none;
    border-top: 1px solid #ccc;
}

.create-account-btn {
    width: 100%;
    padding: 10px;
    background-color: #42b72a;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
}
</style>
