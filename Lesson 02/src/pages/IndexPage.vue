<template>
  <q-page class="flex flex-center">
    <div class="inline-block">     
      <div>
        <q-btn glossy icon="send" icon-right="mail" color="primary" label="button" />
      </div>
      <div class="q-py-md">
        <q-btn push round icon="directions_boat" color="green" />
      </div>
      <div class="q-py-md">
        <q-btn disable round>
          <q-avatar size="50px">
            <img src="../assets/quasar-logo-vertical.svg">
          </q-avatar>
        </q-btn>
      </div>
      <div class="q-py-md">
        <q-btn flat rounded label="Button" color="secondary" />
      </div>
      <div class="q-py-md">
        <q-btn-group push>
          <q-btn color="accent" push icon="send" />
          <q-btn color="accent" push icon="mail" />
          <q-btn color="accent" push icon="directions_boat" />
        </q-btn-group>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage'
})
</script>
