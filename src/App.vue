<template>
  <div class="root">
    <Logo />
    <div id="app" :class="{ 'is-cold': isCold }">
      <div class="row">
        <div class="col-6 celsius-section">
          <Input
            v-on:convert-value="convertToFahrenheit"
            :value="celsius"
            name="celsius"
            id="celsius_input"
            autofocus
          />
          <label for="celsius_input">Celsius</label>
        </div>
        <div class="col-6 fahrenheit-section">
          <Input
            v-on:convert-value="convertToCelsius"
            :value="fahrenheit"
            name="fahrenheit"
            id="fahrenheit_input"
          />
          <label for="fahrenheit_input">Fahernheit</label>
        </div>
      </div>
    </div>
    <Message :isCold="isCold" />
  </div>
</template>

<script>
import Logo from "./components/Logo";
import Input from "./components/Input";
import Message from "./components/Message";

export default {
  name: "app",
  data: () => ({
    celsius: 1,
    fahrenheit: 33.8,
    isCold: true
  }),
  components: {
    Logo,
    Input,
    Message
  },
  methods: {
    convertToFahrenheit: function(newCelsius) {
      this.celsius = newCelsius;
      this.fahrenheit = (this.celsius * (9 / 5) + 32).toFixed(1);
      this.isCold = this.celsius > 30 ? false : true;
    },
    convertToCelsius: function(newFahrenheit) {
      this.fahrenheit = newFahrenheit;
      this.celsius = ((this.fahrenheit - 32) * (5 / 9)).toFixed(1);
      this.isCold = this.celsius > 30 ? false : true;
    }
  }
};
</script>

<style lang="scss">
// Colors
$primary-color: #f6554d;
$secondary-color: #132f63;

* {
  box-sizing: border-box;
}

body,
.root {
  width: 100%;
  height: 100vh;
  min-height: 700px;
  margin: 0;
  font-family: "Muli", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app {
  text-align: center;
  color: #2c3e50;
  height: 100%;

  &.is-cold {
    .celsius-section {
      background: url(./assets/left-bg-blue.png) center left no-repeat;
      * {
        color: $secondary-color;
      }
      input {
        border-color: rgba($secondary-color, 0.5);
        &:focus {
          border-color: $secondary-color;
        }
      }
    }
    .fahrenheit-section {
      background: url(./assets/right-bg.png) center right no-repeat,
        $secondary-color;
    }
  }
}

.row {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;

  @media (max-width: 668px) {
    flex-direction: column;
    .col-6 {
      width: 100% !important;
    }
  }

  .col-6 {
    width: 50%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    label {
      font-size: 64px;
      letter-spacing: 3px;
      margin-top: 24px;
      @media (max-width: 868px) {
        font-size: 48px;
      }
      @media (max-width: 568px) {
        font-size: 28px;
        font-weight: 700;
      }
    }
  }
}

.celsius-section {
  background: url(./assets/left-bg-red.png) center left no-repeat;
  * {
    color: $primary-color;
  }
}
.fahrenheit-section {
  background: url(./assets/right-bg.png) center right no-repeat, $primary-color;
  * {
    color: white;
  }
  input {
    border-color: rgba(white, 0.5);
    &:focus {
      border-color: rgba(white, 1);
    }
  }
}
</style>
