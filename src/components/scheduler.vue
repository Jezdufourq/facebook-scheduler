<template>
    <div>
        <q-card>
            <q-card-section>
                <div class="text-h4 text-bold text-black">
                    Enter your scheduling details
                </div>
                <div>
                    <q-input color="secondary" v-model="person" label="Person to message" />
                    <q-input color="secondary" v-model="message" label="Message you would like to send" />
                </div>
                <div>
                    <div class="q-pa-md" style="max-width: 300px">
                        <q-input filled v-model="date">
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
                </div>
            </q-card-section>
            <q-card-actions align="right">
                <q-btn icon="add" color="secondary"/>
            </q-card-actions>
        </q-card>
    </div>
</template>
<script>

export default {
  name: 'scheduler',
  data () {
    return {
      person: '',
      message: '',
      date: Date.now()
    }
  }
}
</script>
