<template>
    <div class="container d-flex flex-column align-items-center justify-content-center vh-100">
  <div class="card">
    <div class="card-header">
      <h1 class="card-title">CeeBee</h1>
    </div>
    <div class ="card-body">
      <input type="file" @change="handleFileUpload" accept="image/*,video/*" class="form-control" />
      <input type="text" v-model="textInput" placeholder="Saisissez votre texte ici" class="form-control" />
      <label>
        <input type="checkbox" v-model="showPseudo" />
        Afficher Pseudo ?
      </label>
      <div class="checkbox-list">
        <label v-for="name in names" :key="name">
          <input type="checkbox" v-model="selectedNames" :value="name" />
          {{ name }}
        </label>
      </div>
      <div class="duration-inputs">
        <input type="number" v-model="durationSec" placeholder="Durée en s" class="form-control" />
        <input type="number" v-model="durationMs" placeholder="en ms" class="form-control" />
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            textInput: '',
            showPseudo: false,
            names: ['Aëlys', 'Alexis', 'Logan', 'Mattéo'],
            selectedNames: [],
            durationSec: null,
            durationMs: null
        };
    },
    methods: {
        handleFileUpload(event) {
            const file = event.target.files[0];
            if (file) {
                console.log('Fichier uploadé:', file.name);
            }
        }
    }
};
</script>

<style scoped>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.container {
    max-width: 600px;
    width: 90%; /* Responsive width */
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column; /* Stack elements vertically */
}

h1 {
    text-align: center;
    color: #333;
}

input[type="file"],
input[type="text"],
input[type="number"] {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.checkbox-list {
    margin: 10px 0;
}

.checkbox-list label {
    display: block;
}

.duration-inputs {
    display: flex;
    justify-content: space-between;
}

.duration-inputs input {
    width: 48%;
}
</style>