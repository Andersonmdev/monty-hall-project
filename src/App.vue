<template>
  <div id="app">
    <h1>Monty Hall Show!</h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmount">Quantas portas?</label>
        <input
          type="number"
          id="portsAmount"
          size="3"
          v-model.number="portsAmount"
        />
      </div>
      <div v-if="!started">
        <label for="portsAmount">Qual a porta é premiada?</label>
        <input
          type="number"
          id="portsAmount"
          size="3"
          v-model.number="selectedPort"
        />
      </div>
      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" :key="i">
        <Door :hasGift="i == selectedPort" :number="i" />
      </div>
    </div>
    <footer class="footer">
      <a href="https://github.com/Andersonmdev" target="_blank"
        >Develop by Andersonmdev</a
      >
      <a
        href="https://www.flaticon.com/free-icons/gift"
        title="gift icons"
        target="_blank"
      >
        Gift icons created by Freepik - Flaticon
      </a>
    </footer>
  </div>
</template>

<script>
import Door from "./components/Door";

document.title = "Monty Hall Show";

export default {
  name: "App",
  components: { Door },
  data: function () {
    return {
      started: false,
      portsAmount: 3,
      selectedPort: null,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  color: #fff;
  background: linear-gradient(to right, #005aa7, #fffde4);
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 98vh;
}

#app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 20px;
  margin-bottom: 60px;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}

.form,
.form input,
.form button {
  margin-bottom: 10px;
  font-size: 2rem;
}

.form input {
  width: 80px;
  margin-left: 10px;
  border-radius: 10px;
  text-align: center;
}

.form button {
  border-radius: 10px;
  padding: 10px 20px;
  background-color: #0004;
  color: #fff;
  border: none;
  cursor: pointer;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;

  flex-wrap: wrap;
}

.footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: auto;
}

.footer a {
  color: #fff;
  text-decoration: none;
}
</style>
