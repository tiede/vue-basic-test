<template>
  <div>
    <div>Hello {{value}}</div>
    <div>Current Weather in Copenhagen: {{currentWeather.temp_c}}</div>
    <div>Current Weather in Copenhagen (feels like): {{currentWeather.feelslike_c}}</div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      value: "World",
      currentWeather: {},
    };
  },

  methods: {
    async getWeatherData() {
      const res = await fetch('https://api.weatherapi.com/v1/current.json?key=3de6c9f8c2504acaa36202353230902&q=Copenhagen&aqi=no');
      const finalRes = await res.json();
      this.currentWeather = finalRes.current;
    }
  },
  mounted() {
    this.getWeatherData()
  }
};

</script>