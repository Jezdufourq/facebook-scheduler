<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-white">
      <div class="row justify-center">
        <div class="col-auto text-h1 text-bold text-black">
          SCHEDULER
        </div>
      </div>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  data () {
    return {
    }
  }
}
</script>
