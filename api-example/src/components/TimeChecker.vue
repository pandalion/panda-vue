<template>
  <div>
    <h1>{{ title }}</h1>
    <h2>Please choose a country</h2>
    <!-- to-do: add loading spinner to show locations are loading -->
    <select>
        <option v-for="zone in timezones" :value="zone.value" :key="zone.id">
            {{ zone }}
        </option>
    </select>
    <p>Selected: Show selected timezone here</p>
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
    this.axios.get('http://worldtimeapi.org/api/timezone/').then(response => (this.timezones = response.data))
    .catch(error => console.log(error));
  }
}
</script>

<style scoped lang="scss">
// time-checker specific styles here
</style>
