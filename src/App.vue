<template>
  <b-container fluid id="app" class="h-100">
    <modalcomponent />
    <b-container fluid class="p-0">
      <b-row class="bg-primary py-4 px-0 px-sm-4">
        <b-col sm="9" class="text-light">
          <h1 class="display-4">{{ h1 }}</h1>
          <span class="lead">{{ desc }}</span>
        </b-col>
        <b-col sm="3" class="text-center text-sm-right text-light mt-2 mt-sm-0">
          <b-nav fill>
            <b-nav-item class="d-inline-block text-center" v-b-modal.modal1><i class="far mx-auto fa-question-circle fa-fw fa-4x text-white d-block"></i><span class="d-block text-white">Requirements</span></b-nav-item>
            <b-nav-item class="d-inline-block text-center" href="https://github.com/Adamkillander96/instant-app-maker" target="_blank"><i class="fab mx-auto fa-github fa-fw fa-4x d-block text-white"></i><span class="d-block text-white">GitHub</span></b-nav-item>
          </b-nav>
        </b-col>
      </b-row>
      <b-row>
        <b-col lg="5" class="bg-light shadow-ct">
          <b-row class="p-0 p-md-4">
            <b-col v-for="(input, index) in inputs" :key="input.title" md="6">
              <div class="p-2 mb-4">
                <label class="lead" :for="`meta${index}`" v-b-tooltip.hover :title="input.description">{{ input.title }}:</label>
                <b-input-group v-if="!input.options">
                  <b-form-input class="border-0 shadow-sm bg-white" :id="`meta${index}`" :type="input.type" :placeholder="input.placeholder" v-model="input.value" :value="input.value"></b-form-input>
                </b-input-group>
                <b-form-select class="border-0 shadow-sm bg-white" v-if="input.options" v-model="input.value" :options="input.options"/>
                <i v-if="input.title == 'Orientation'" class="fas fa-mobile-alt"></i>
              </div>
            </b-col>
          </b-row>
        </b-col>
        <b-col lg="7">
          <b-tabs class="nav-fill mt-2" pills>
            <b-tab title="HTML header code" active>
              <div id="Html" class="bg-white mt-2">
                <code v-if="!wpToggle" class="d-block mb-2 text-success">Copy and paste this into your HTML header</code>
                <code v-if="wpToggle" class="d-block mb-2 text-success">Add this to your functions.php file"</code>
                <hr>
                <b-btn v-on:click='wpToggle = !wpToggle' :class="{'active' : wpToggle == true}" size="sm" variant="primary"><i class="fab fa-wordpress-simple"></i> Wordpress version</b-btn>
                <code v-if="wpToggle" class="d-block mt-2 mb-2 text-primary" v-text="`function adams_app_metadata() { ?>`"></code>
                <metacomponent v-bind:inputs="inputs" />
                <code v-if="wpToggle" class="d-block mb-2 text-primary" v-text="`<?php } add_action( 'wp_head', 'adams_app_metadata' );`"></code>
              </div>
            </b-tab>
            <b-tab title="Manifest json">
              <div id="Manifest" class="bg-white mt-2">
                <code class="d-block mb-2 text-success">Create a document called manifest.json and use this code.</code>
                <hr>
                <manifestcomponent v-bind:inputs="inputs" />
              </div>
            </b-tab>
            <b-tab title="Browserconfig xml">
              <div id="Browserconfig" class="bg-white mt-2">
                <code class="d-block mb-2 text-success">Create a document called browserconfig.xml and use this code.</code>
                <hr>
                <configcomponent v-bind:inputs="inputs" />
              </div>
            </b-tab>
            <b-tab title="Service worker js">
              <div id="SwJs" class="bg-white mt-2">
                <code class="d-block mb-2 text-success">Create a document called sw.js in your root domain and then add the service worker register to the bottom of your page.</code>
                <hr>
                <swcomponent v-bind:inputs="inputs" />
              </div>
            </b-tab>
          </b-tabs>
        </b-col>
      </b-row>
    </b-container>
  </b-container>
</template>

<script>
import modalcomponent from './modal/modal.vue'
import metacomponent from './tags/meta.vue'
import manifestcomponent from './tags/manifest.vue'
import configcomponent from './tags/browserconfig.vue'
import swcomponent from './tags/sw.vue'
export default {
  name: 'app',
  components: { 
    modalcomponent,
    metacomponent,
    manifestcomponent,
    configcomponent,
    swcomponent
  },
  data () {
    return {
      h1: 'The Instant App Maker',
      desc: 'Turn your website into a downloadable app (PWA, Progressive Web Application) in no time!',
      wpToggle: false,
      inputs: [
        { title: 'Title', description: 'This is the full name of your app', type: 'text', value:'', placeholder: 'The Best App Ever' },
        { title: 'Short title', description: 'This is the short name of your app', type: 'text', value:'', placeholder: 'Best App' },
        { title: 'Description', type: 'text', value:'', placeholder: 'Simply the best on planet earth' },
        { title: 'Theme-color', description: 'Provide the apps color in HEX', type: 'text', value:'', placeholder: '#333333' },
        { title: 'Apple status bar', description: 'Apple gives you 3 choices.', type: 'text', value:'Please select an option', placeholder: 'Select...', options: ['Please select an option', 'default', 'black', 'black-translucent']},
        { title: 'Image', description: 'The image must be in PNG format', type: 'url', placeholder: 'https://example.com/image.png' },
        { title: 'SVG', description: 'The image must be in SVG format', type: 'url', placeholder: 'https://example.com/image.svg' },
        { title: 'Orientation', description: 'Select what how the app will be presented', type: 'text', value:'Please select an option', placeholder: 'Select...', options: ['Please select an option', 'any', 'landscape', 'portrait']},
        { title: 'Display', description: 'Decide what UI elememts to show', type: 'text', value:'Please select an option', placeholder: 'Select...', options: ['Please select an option', 'fullscreen', 'standalone', 'browser']},
        { title: 'Domain', description: 'Write your domain name', type: 'url', value:'', placeholder: 'https://yourdomainname.com' }
      ]
    }
  }
}
</script>

<style lang="scss">
@import '/assets/custom-variables.scss';
@import '../node_modules/bootstrap/scss/bootstrap.scss';
@import '/assets/custom-classes.scss';

select {
  -moz-appearance: none;
  -webkit-appearance: none;
}
select::-ms-expand {
  display: none;
}
</style>
