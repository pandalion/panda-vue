<template>
  <div>
    <h1>{{ title }}</h1>
    {{ info }}
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
      info: null
    }
  },
  mounted () {
    this.axios.get('http://worldtimeapi.org/api/').then(response => (this.info = response));
  }
}
</script>

<style scoped lang="scss">
// time-checker specific styles here
</style>
