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
          <scheduler />
        </q-dialog>
    </div>
</template>

<script>
import { date } from 'quasar'
import Scheduler from './scheduler'

export default {
  name: 'tableScheduler',
  components: {
    Scheduler
  },
  data () {
    return {
      dialogOpen: false,
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
        {
          name: 'Test Name',
          person: 'Test Person',
          date: date.formatDate(Date.now(), 'YYYY-MM-DD HH:mm')
        }
      ]
    }
  },
  methods: {
    openDialog () {
      this.dialogOpen = true
      console.log('dialog opened')
    }
  }
}
</script>
