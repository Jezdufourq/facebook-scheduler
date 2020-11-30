<template>
    <div class="q-pa-md">
        <q-card>
          <q-card-section>
            <div class="row justify-between">
              <div class="text-h5 text-bold">
                CURRENT SCHEDULES
              </div>
              <div>
                <q-btn icon="add" color="primary" @click="openDialog"/>
              </div>
            </div>
          </q-card-section>
          <q-table
          :data="data"
          :columns="columns"
          row-key="name"
          flat
          bordered
          />
        </q-card>
        <q-dialog v-model="dialogOpen">
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
                <q-btn icon="add" color="primary" @click="submitData" />
            </q-card-actions>
        </q-card>
        </q-dialog>
    </div>
</template>

<script>
import { date } from 'quasar'

export default {
  name: 'tableScheduler',
  data () {
    return {
      dialogOpen: false,
      name: '',
      person: '',
      message: '',
      date: date.formatDate(Date.now(), 'YYYY-MM-DD HH:mm'),
      columns: [
        {
          name: 'name',
          required: true,
          label: 'Scheduler name',
          align: 'left',
          field: row => row.name,
          format: val => `${val}`,
          sortable: true
        },
        {
          name: 'Person',
          align: 'center',
          label: 'Person',
          field: 'person',
          sortable: true
        },
        {
          name: 'Schedule Date',
          align: 'center',
          label: 'Schedule Date',
          field: 'date',
          sortable: true
        }
      ],
      data: [
      ]
    }
  },
  methods: {
    openDialog () {
      this.dialogOpen = true
      console.log('dialog opened')
    },
    submitData () {
      this.data.push({
        name: this.name,
        person: this.person,
        date: this.date
      })
      console.log('obj: ' + JSON.stringify({
        name: this.name,
        person: this.person,
        date: this.date
      }))
      // closing dialog + resetting data
      this.openDialog = false
      this.name = ''
      this.person = ''
      this.message = ''
      this.date = null
    }
  }
}
</script>
