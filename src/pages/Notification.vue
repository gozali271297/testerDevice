<template>
  <q-page class="container">
    <cp-head title="Notification" icon="notification_important" chrome firefox safari opera android apple></cp-head>
    <div class="row items-center justify-center" style="height: 80vh">
      <div class="col-10 text-center">
        <span class="text-subtitle1 text-weight-medium text-negative">Funcionamento atual somente em desktop</span>
        <q-btn
          color="primary"
          icon="notification_important"
          label="Notification"
          class="full-width"
          size="lg"
          @click="notification()" />
      </div>
    </div>
  </q-page>
</template>

<style>
</style>

<script>
import CpHead from 'components/CpHead'
export default {
  name: 'PageGeolocation',
  components: {
    CpHead
  },
  data () {
    return {
      text: 'Opa! Essa é uma notificação! =)',
      img: 'statics/quasar-web-apis.png'
    }
  },
  methods: {
    notification () {
      Notification.requestPermission((status) => {
        if (Notification && Notification.permission === 'granted') {
          let n = new Notification('Notificação', { body: this.text })
          console.log(n) // eslint-disable-line no-console
        }
      })
    },
    errorPosition () {
      this.$q.notify({
        position: 'top',
        timeout: 2500,
        color: 'negative',
        textColor: 'white',
        actions: [{ icon: 'close', color: 'white' }],
        message: 'Não foi possível obter a localização.'
      })
    }
  }
}
</script>
