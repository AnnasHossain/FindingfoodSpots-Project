<template>
  <div class="about">
    <div class="content">
      <img class="company-image" src="../assets/company-image.jpg" alt="Company Image">
      <h1 class="title">About Us</h1>
      <p>Welcome to our company website. Learn more about who we are and what we do.</p>

    </div>
    <div class="login-form">
      <h2 class="login-title">Log In to Our Website</h2>
      <div class="input-group">
        <input type="text" v-model="name" class="login-input" placeholder="Enter Name" />
      </div>
      <button type="button" class="login-btn" @click="login">Log In</button>
      <p v-if="showErrorMessage" class="error-message">The user does not exist. Please register.</p>
      <hr class="divider" />
      <button type="button" class="create-nutzer-btn" @click="createUserButton">Create New User</button>
      <p v-if="showGagErrorMessage" class="error-message">This button is a gag...</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      Nutzer: [],
      name: '',
      showErrorMessage: false,
      showGagErrorMessage: false, // Wenn ich eine neue Funktion in vue nutzen will muss ich sie auch in data() deklarieren
    };
  },
  methods: {
    login() {
      fetch(process.env.VUE_APP_BACKEND_BASE_URL + "/Nutzers")
          .then((response) => response.json())
          .then((Nutzer) => {
            const foundNutzer = Nutzer.find((Nutzers) => Nutzers.name === this.name);

            if (!foundNutzer) {
              this.showErrorMessage = true;
              return;
            }
            this.$router.push("/foodspots");
          })
          .catch((error) => {
            console.error("Failed to retrieve user data:", error);
          });
    },
    createUserButton() {
      this.showGagErrorMessage = true;
    },
  },
  mounted() {
    const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/Nutzers'
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }
    fetch(endpoint, requestOptions)
        .then(response => response.json())
        .then (result => result.forEach(nutzer => {
          this.Nutzer.push(nutzer)
        }))
        .catch(error => console. log('error', error));
  }
};
</script>


<style scoped>
.about {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f0f2f5;
}

.content {
  text-align: center;
  margin: 30px;
}

.title {
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 20px;
}

.login-form {
  max-width: 400px;
  margin: 20px;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  background-color: #fff;
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
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  box-sizing: border-box;
}

.login-btn {
  width: 100%;
  padding: 12px;
  background-color: #1877f2;
  color: #fff;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s;
}

.login-btn:hover {
  background-color: #1659a3;
}

.error-message {
  color: red;
  font-size: 14px;
  margin-top: 16px;
}

.divider {
  margin: 16px 0;
  border: none;
  border-top: 1px solid #ccc;
}

.create-nutzer-btn {
  width: 100%;
  padding: 12px;
  background-color: #42b72a;
  color: #fff;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s;
}

.company-image {
  margin-top: 20px;
  max-width: 100%;
  width: 90%;
  height: auto;
}

.create-nutzer-btn:hover {
  background-color: #399523;
}
</style>
