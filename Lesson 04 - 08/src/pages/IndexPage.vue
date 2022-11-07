<template>
  <q-page class="flex flex-center">
    <q-btn label="Alert" color="primary" @click="alert = true" />
    <q-btn label="Top" icon="keyboard_arrow_up" color="primary" @click="top = true" />

    <q-dialog v-model="alert">
      <q-card>
        <q-card-section>
          <div class="text-h6">Alert</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis perferendis totam, ea at omnis vel numquam exercitationem aut, natus minima, porro labore.
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="OK" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <q-dialog v-model="top" position="top">
      <q-card>
        <q-card-section>
          <div class="text-h6">Alert</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis perferendis totam, ea at omnis vel numquam exercitationem aut, natus minima, porro labore.
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="OK" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <q-table
      class="my-sticky-header-table"
      title="Treats"
      :rows="rows"
      :columns="columns"
      table-header-class="text-brown"
      card-class="text-brown"
      row-key="name"
      flat
      dark
      bordered
    />
    <div class="q-px-md">
      <q-card style="...">
        <q-card-section>
          <q-list separator>
            <q-item clickable v-ripple>
               <q-item-section top avatar>
                <q-avatar color="teal" text-color="white" icon="home" />
              </q-item-section>
              <q-item-section>
                 <q-item-label>Single line item</q-item-label>
                 <q-item-label caption>Secondary line text. Lorem ipsum dolor sit amet,<br/> consectetur adipiscit elit.</q-item-label>
              </q-item-section>         
            </q-item>

            <q-item clickable v-ripple :active="true">
              <q-item-section top avatar>
                <q-avatar round>
                  <img src="https://i.pinimg.com/474x/ac/d0/24/acd0246188509d0090a97241e39a693f.jpg">
                </q-avatar>
              </q-item-section>
              <q-item-section>
                 <q-item-label>Marisus</q-item-label>
                 <q-item-label caption>Normal witch</q-item-label>
              </q-item-section>
              <q-item-section side top>
                 <q-item-label caption>Online</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-card-section>
      </q-card>
    </div>
    <div style="max-width: 300px" class="bg-grey-10 text-white">
      <q-list bordered icon="home" label="home" caption="">
        <q-expansion-item
        header-class="text-orange"
        expand-separator
        icon="perm_identity"
        label="Account settings"
        caption="John Doe">
          <q-card  class="bg-grey-9">
            <q-card-section>
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem, eius reprehenderit eos corrupti
            commodi magni quaerat ex numquam, dolorum officiis modi facere maiores architecto suscipit iste
            eveniet doloribus ullam aliquid.
            </q-card-section>
          </q-card>
        </q-expansion-item>
        <q-expansion-item header-class="text-purple" v-model="expandItem" expand-separator icon="mail" label="Mail">
          <q-icon name="mail" size="50px"></q-icon>
        </q-expansion-item>
      </q-list>
    </div>
    <div>
      <q-btn label="Click me!" @click="expandItem = !expandItem" />
    </div>
    <q-fab vertical-actions-align="left" label="options" color="blue" icon="keyboard_arrow_down" direction="down" :hide-label="hideLabel">
      <q-fab-action label="Mail" color="red" icon="mail" :hide-label="hideLabel" />
      <q-fab-action label="Home" color="orange" icon="home" :hide-label="hideLabel" />
    </q-fab>
    <q-btn :ripple="false" color="deep-orange" push @click="hideLabel = !hideLabel, showFabButton = !showFabButton" label="Hide FAB Labels" v-if="showFabButton"/>
    <q-btn :ripple="false" color="deep-orange" push @click="hideLabel = !hideLabel, showFabButton = !showFabButton" label="Show FAB Labels" v-if="!showFabButton"/>
     <div class="q-pa-md flex flex-center">
    <q-circular-progress
      indeterminate
      rounded
      size="50px"
      color="lime"
      class="q-ma-md"
    />
     </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data() {
    return {
      showFabButton: true,
      expandItem: false,
      alert: false,
      top: false,
      hideLabel: false,
      columns: [
        {
          name: 'firstname',
          label: 'First Name',
          field: 'firstName'
        },
        {
          name: 'lastname',
          label: 'Last Name',
          field: 'lastName'
        }
      ],
      rows: [
        {
          firstName: 'Floren',
          lastName: 'tino'
        },
        {
          firstName: 'Hieu',
          lastName: 'Vux'
        },
        {
          firstName: 'Quang',
          lastName: 'Vux'
        },
        {
          firstName: 'Le',
          lastName: 'Tan'
        },
        {
          firstName: 'Duy',
          lastName: 'Manh'
        },

        {
          firstName: 'Duc',
          lastName: 'Nguyen'
        },
        {
          firstName: 'Thanh',
          lastName: 'Tung'
        },
        {
          firstName: 'The',
          lastName: 'Giau'
        },
        {
          firstName: 'Quang',
          lastName: 'Nguyen'
        },
        {
          firstName: 'Tran',
          lastName: 'Kien'
        },
        {
          firstName: 'Tuan',
          lastName: 'Anh'
        },
      ]
    }
  },
})
</script>
<style lang="sass">
.my-sticky-header-table
  height: 310px

.q-table__top,
.q-table__bottom,
  thead tr:first-child th
  background-color: $blue-2

thead tr th
  position: sticky
  z-index: 1
thead tr:first-child th
  top: 0

.q-table--loading thead tr:last-child th
  top: 48px
</style>
