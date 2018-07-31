<template>
  <b-container fluid id="app" class="h-100">
    <b-modal id="modal1" title="Bootstrap-Vue">
      <p class="my-4">Hello from modal!</p>
    </b-modal>
    <b-container fluid class="p-0">
      <b-row class="bg-primary p-4 shadow">
        <b-col sm="9" class="text-light">
          <h1 class="display-4">{{ h1 }}</h1>
          <span class="lead">{{ desc }}</span>
        </b-col>
        <b-col sm="3" class="text-center text-sm-right text-light mt-4 mt-sm-0">
          <a class="text-light d-inline-block text-center" v-b-modal.modal1><i class="far mx-auto fa-question-circle fa-fw fa-4x d-block"></i><span class="d-block">Requirements</span></a>
          <a class="text-light d-inline-block text-center" href="https://github.com/Adamkillander96/instant-app-maker" target="_blank"><i class="fab mx-auto fa-github fa-fw fa-4x d-block"></i><span class="d-block">GitHub</span></a>
        </b-col>
      </b-row>
      <b-row class="mt-5 px-0 px-sm-5">
        <b-col lg="6">
          <b-row class="my-1">
            <b-col v-for="(input, index) in inputs" :key="input.title" md="6">
              <div class="p-2 mb-4 shadow-sm rounded">
                <label class="lead" :for="`meta${index}`" v-b-tooltip.hover :title="input.description">{{ input.title }}:</label>
                <b-input-group v-if="!input.options">
                  <b-form-input class="border-0 shadow-sm bg-light" :id="`meta${index}`" :type="input.type" :placeholder="input.placeholder" v-model="input.value" :value="input.value"></b-form-input>
                </b-input-group>
                <b-form-select class="border-0 shadow-sm bg-light" v-if="input.options" v-model="input.value" :options="input.options"/>
                <i v-if="input.title == 'Orientation'" class="fas fa-mobile-alt"></i>
              </div>
            </b-col>
          </b-row>
        </b-col>
        <b-col class="shadow" lg="6">
          <h2 class="mt-4">Code</h2>
          <hr>
          <b-tabs fill pills>
            <b-tab title="Raw code" active>
              <div id="Raw" class="p-2 bg-white mt-2">
                <code class="d-block mb-2 text-success">// Copy and paste this into your HTML header"</code>
                <metacomponent v-bind:inputs="inputs" />
              </div>
            </b-tab>
            <b-tab title="Wordpress Code">
              <div id="Wp" class="p-2 bg-white mt-2">
                <code class="d-block mb-2 text-success">// Add this to your functions.php file"</code>
                <code class="d-block mb-2 text-primary" v-text="wp.firstline"></code>
                <metacomponent v-bind:inputs="inputs" />
                <code class="d-block mb-2 text-primary" v-text="wp.secondline"></code>
              </div>
            </b-tab>
          </b-tabs>
        </b-col>
      </b-row>
    </b-container>
  </b-container>
</template>

<script>
import metacomponent from './meta/tags.vue'
export default {
  name: 'app',
  components: { 
    metacomponent,
  },
  data () {
    return {
      h1: 'The Instant App Maker',
      desc: 'Turn your website into a downloadable app in no time!',
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
        
      ],
      wp: { 
        firstline: "function adams_app_metadata() { ?>",
        secondline: "<?php } add_action( 'wp_head', 'adams_app_metadata' );"
      }
    }
  }
}
</script>

<style lang="scss">
@import '/assets/custom-variables.scss';
@import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>
