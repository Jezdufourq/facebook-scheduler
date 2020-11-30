<template>
  <q-page class="flex flex-center">
    <scheduler />
  </q-page>
</template>

<script>
import Scheduler from 'src/components/scheduler.vue'
export default {
  name: 'PageIndex',
  components: {
    Scheduler
  }
}
</script>
