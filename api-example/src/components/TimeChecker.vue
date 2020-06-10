<template>
  <div>
    <h1>{{ title }}</h1>

    <section>
        <h2>Please choose a country</h2>
        <!-- to-do: add loading spinner to show locations are loading -->
        <select>
            <option v-for="zone in timezones" :value="zone.value" :key="zone.id">
                {{ zone }}
            </option>
        </select>
        <p>Selected: Show selected timezone here</p>
    </section>

    <section>
        <h2>Please choose a location</h2>
        <p>Display list of locations filtered by main area chosen above</p>
    </section>

    <section>
        <h3>Your time is: <span>XX:XX</span> </h3>
    </section>
  </div>
</template>

<script>
export default {
  name: 'TimeChecker',
  props: {
    title: String
  },
  data () {
    return {
      timezones: null
    }
  },
  mounted () {
    // get the relevant bits we need from the API
    // to-do: this should be showing area only for our first dropdown
    this.axios.get('http://worldtimeapi.org/api/timezone/').then(response => (this.timezones = response.data))
    .catch(error => console.log(error));
  }
}
</script>

<style scoped lang="scss">
section {
    border-top: 1px solid #ccc;
}
* + section {
    margin-top: 30px;
}
h3 span {
    // this would use variable when we have the global variables file
    color: teal;
    font-size: 30px;
}
</style>
