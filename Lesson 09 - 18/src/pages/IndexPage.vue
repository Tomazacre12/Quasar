<template>
  <q-page>
    <div>
      <q-card style="max-width: 500px">
        <q-item>
          <q-item-section avatar>
            <q-skeleton type="QAvatar" />
          </q-item-section>
          <q-item-section>
            <q-item-label>
              <q-skeleton type="text" />
            </q-item-label>
            <q-item-label caption>
              <q-skeleton type="text" />
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-skeleton height="200px" square />

        <q-card-actions align="right" class="q-gutter-md">
          <q-skeleton type="QBtn" />
          <q-skeleton type="QBtn" />
        </q-card-actions>
      </q-card>
    </div>
    <div class="flex q-pa-md">

        <div>
          <q-spinner-audio
            color="primary"
            size="2em"
          />
          <q-tooltip :offset="[0, 8]">QSpinnerAudio</q-tooltip>
        </div>
      <div  style="max-width: 300px">
        <q-tabs v-model="tabs" outside-arrows class="bg-primary text-white shadow-2" dense>
          <q-tab name="home" label="Home" icon="home" />
          <q-tab name="mail" label="Mail" icon="mail">
            <q-badge color="red" floating>2</q-badge>
          </q-tab>
          <q-tab name="movies" icon="movie" label="Movies">
            <q-badge color="red" floating>10+</q-badge>
          </q-tab>
          <q-tab name="photos" icon="photo" label="Photos" />
          <q-tab alert="red" name="videos" label="Videos" icon="slow_motion_video" />
          <q-btn-dropdown auto-close stretch flat label="More...">
            <q-list>
              <q-item clickable>
                <q-item-sections>ALARMS</q-item-sections>
              </q-item>
              <q-item clickable>
                <q-item-sections>ADDRESS BOOK</q-item-sections>
              </q-item>
            </q-list>
          </q-btn-dropdown>
        </q-tabs>
      </div>
      <div>
        <q-tab-panels class="bg-purple-1 text-center" v-model="tabs" animated>
          <q-tab-panel name="photos">
            <div class="text-h6">Photos</div>
            Lorem ispum dolor sit amet consectetur adipisicing elit.
          </q-tab-panel>
          <q-tab-panel name="mail">
            <div class="text-h6">Mail</div>
            Lorem ispum dolor sit amet consectetur adipisicing elit.
          </q-tab-panel>
          <q-tab-panel name="movies">
            <div class="text-h6">Movies</div>
            Lorem ispum dolor sit amet consectetur adipisicing elit.
          </q-tab-panel>
        </q-tab-panels>
      </div>
      <div>
          <q-spinner-audio
            color="primary"
            size="2em"
          />
          <q-tooltip :offset="[0, 8]">QSpinnerAudio</q-tooltip>
        </div>
    </div>
    <div class="q-pa-md" style="width: 400px">
      <q-carousel
        v-model="carousel"
        transition-prev="jump-right"
        transition-next="jump-left"
        prev-icon="arrow_left"
        next-icon="arrow_right"
        navigation-icon="radio_button_unchecked"
        swipeable
        animated
        control-color="white"
        navigation
        padding
        arrows
        height="300px"
        class="bg-primary text-white shadow-1 rounded-borders"
        infinite
        :autoplay="autoplay"
        ref="carousel"
      >
        <q-carousel-slide name="Home" class="column no-wrap flex-center">
          <div class="text-h2 text-white">
            Home
          </div>
          <div>
            {{lorem}}
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="Mail" class="column no-wrap flex-center">
          <div class="text-h2 text-white">
            Mail
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="Profile" class="column no-wrap flex-center">
          <div class="text-h2 text-white">
            Profile
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="Settings" class="column no-wrap flex-center">
          <div class="text-h2 text-white">
            Settings
          </div>
        </q-carousel-slide>    
        <template v-slot:control>
          <q-carousel-control
            position="top-right"
            :offset="[18, 18]"
            class="text-white rounded-borders"
            style="background: rgba(0, 0, 0, .3); padding: 4px 8px;"
          >
            <q-toggle dense dark color="orange" v-model="autoplay" label="Auto Play" />
          </q-carousel-control> 
        </template>
      </q-carousel>
    </div>  
    <div class="q-pa-md">
      <div style="max-width: 300px">
        <q-form @submit="submitForm">
          <div>
            <q-input 
            standout
            clearable 
            clear-icon="close"
            color="teal"
            label="your name"
            v-model="formData.textInput"
            :rules="[val => !!val || 'Field is required']"
            > 
              <template v-slot:append>
                 <q-avatar>
                    <img src="https://cdn.quasar.dev/logo-v2/svg/logo.svg">
                 </q-avatar>
              </template>
            </q-input>
            <q-select 
            standout
            color="teal"
            :rules="[val => !!val || 'Field is required']"
            v-model="formData.multiChoices" 
            :options="formData.multi" 
            transition-show="jump-up"
            transition-hide="jump-down"
            label="Select multiple values"
            use-input
            use-chips
            multiple
            >
              <template v-slot:append>
                <q-icon name="person" />
              </template>
            </q-select>
            <div>
              <span>Gender:</span>
              <q-radio v-model="formData.sex" color="teal" val="Male" label="Male" />
              <q-radio v-model="formData.sex" color="red" val="Female" label="Female" />
              <q-radio v-model="formData.sex" color="pink" val="LGBT" label="LGBT" />
            </div>
          </div>
          <div>
            <q-checkbox true-value="yes" color="teal" false-value="no" v-model="formData.hunger" @click="showFood" label="Are you hungry ?" />
          </div>
          <div v-if="showFoodState">
            <q-list>
              <q-item>
                <q-item-section avatar>
                  <q-item-label>
                    <q-checkbox color="blue" val="mayo" v-model="formData.choices"  />
                  </q-item-label>
                </q-item-section>
                <q-item-section>
                  <q-item-label>
                    Mayo
                  </q-item-label>
                  <q-item-label caption>
                    Adds mayo to the food
                  </q-item-label>
                </q-item-section>
              </q-item>
              <q-item>
                <q-item-section avatar>
                  <q-item-label>
                    <q-checkbox color="yellow" val="cheese" v-model="formData.choices"  />
                  </q-item-label>
                </q-item-section>
                <q-item-section>
                  <q-item-label>
                    Cheese
                  </q-item-label>
                  <q-item-label caption>
                    Adds cheese to the food
                  </q-item-label>
                </q-item-section>
              </q-item>
              <q-item>
                <q-item-section avatar>
                  <q-item-label>
                    <q-checkbox color="red" val="spice" v-model="formData.choices"  />
                  </q-item-label>
                </q-item-section>
                <q-item-section>
                  <q-item-label>
                    Spice
                  </q-item-label>
                  <q-item-label caption>
                    Adds spice to the food
                  </q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </div>
          <div class="q-pt-md">
            <q-btn type="submit" push class="glossy" color="black" label="Submit" />
          </div>
        </q-form>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import { ref } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data() {
    return {
      tabs: "home",
      carousel: "Home",
      lorem: "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Itaque voluptatem totam, architecto cupiditate officia rerum, error dignissimos praesentium libero ab nemo.",
      slide: ref(1),
      autoplay: ref(false), 
      showFoodState: false,
      formData: {
        textInput: null,
        multiChoices: null,
        sex: null,
        hunger: "no",
        choices: [],
        options: [
          "Male",
          "Female",
          "LGBT"
        ],
        multi: [
          'Google',
          'Facebook',
          'Twitter',
          'Apple',
          'Oracle'
        ]
      }
    }
  },
  methods: {
    submitForm() {
      alert('Your name is:' + this.formData.textInput + ' ' + 'Your application is:' + this.formData.multiChoices)
    },
    showFood() {
      this.showFoodState = !this.showFoodState
    }
  },
})
</script>
