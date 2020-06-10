<template>
  <div class="home">
    <svg class="icon icon-clock">
        <use xlink:href="#icon-clock"></use>
    </svg>
    <TimeChecker title="Where are you?"/>
  </div>
</template>

<script>
import TimeChecker from '@/components/TimeChecker.vue'

export default {
  name: 'Home',
  components: {
    TimeChecker
  }
}
</script>
