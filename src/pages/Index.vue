<template>
  <q-page class="flex flex-center">
    <!-- <scheduler /> -->
    <table-scheduler />
  </q-page>
</template>

<script>
import tableScheduler from 'src/components/tableScheduler.vue'
// import scheduler from 'src/components/scheduler.vue'

export default {
  name: 'PageIndex',
  components: {
    // scheduler,
    tableScheduler
  }
}
</script>
