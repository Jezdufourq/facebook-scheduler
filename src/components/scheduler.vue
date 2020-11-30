<template>
    <div>
        <q-card>
            <q-card-section>
                <div class="text-h4 text-bold text-black">
                    Enter your scheduling details
                </div>
                <div>
                    <q-input class="q-py-md" color="primary" v-model="name" label="Name of the scheduler" />
                    <q-input class="q-py-md" color="primary" v-model="person" label="Person to message" />
                    <q-input class="q-py-md" color="primary" v-model="message" label="Message you would like to send" />
                    <q-input class="q-py-md" filled v-model="date">
                    <template v-slot:prepend>
                        <q-icon name="event" class="cursor-pointer">
                        <q-popup-proxy transition-show="scale" transition-hide="scale">
                            <q-date v-model="date" mask="YYYY-MM-DD HH:mm">
                            <div class="row items-center justify-end">
                                <q-btn v-close-popup label="Close" color="primary" flat />
                            </div>
                            </q-date>
                        </q-popup-proxy>
                        </q-icon>
                    </template>

                    <template v-slot:append>
                        <q-icon name="access_time" class="cursor-pointer">
                        <q-popup-proxy transition-show="scale" transition-hide="scale">
                            <q-time v-model="date" mask="YYYY-MM-DD HH:mm" format24h>
                            <div class="row items-center justify-end">
                                <q-btn v-close-popup label="Close" color="primary" flat />
                            </div>
                            </q-time>
                        </q-popup-proxy>
                        </q-icon>
                    </template>
                    </q-input>
                </div>
            </q-card-section>
            <q-card-actions align="right">
                <q-btn icon="add" color="primary" @click="submitData"/>
            </q-card-actions>
        </q-card>
    </div>
</template>
<script>

import { date } from 'quasar'

export default {
  name: 'scheduler',
  data () {
    return {
      name: '',
      person: '',
      message: '',
      date: date.formatDate(Date.now(), 'YYYY-MM-DD HH:mm')
    }
  },
  methods: {
    submitData () {
      var updatedScheduler = {
        name: this.name,
        person: this.person,
        message: this.message,
        date: this.date
      }

      console.log('obj: ' + JSON.stringify(updatedScheduler))
      this.$store.commit('updateCurrentSchedulers', updatedScheduler)
    }
  }
}
</script>
