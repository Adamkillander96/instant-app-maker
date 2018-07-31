<template>
  <b-container fluid id="app" class="bg-primary p-4 h-100">
    <b-container class="bg-white p-4">
    <h1>{{ h1 }}</h1>
    <span>{{ desc }}</span>
    <hr>
    <b-row>
      <b-col md="8">
        <b-row class="my-1">
          <b-col v-for="input in input" :key="input.title" md="6">
            <label class="lead" :for="`type-${input.type}`" v-b-tooltip.hover :title="input.description">{{ input.title }}:</label>
            <b-input-group v-if="!input.options">
              <b-form-input :id="`type-${input.type}`" :type="input.type" :placeholder="input.placeholder"></b-form-input>
            </b-input-group>
            <b-form-select v-if="input.options" v-model="input.selected" :options="input.options"></b-form-select >
            <i v-if="input.title == 'Orientation'" class="fas fa-mobile-alt"></i>
          </b-col>
        </b-row>
      </b-col>
    </b-row>
    </b-container>
  </b-container>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      h1: 'The Instant App Maker',
      desc: 'Turn your website into a downloadable app in no time!',
      input: [
        { title: 'Title', description: 'This is the full name of your app', type: 'text', placeholder: 'The Best App Ever' },
        { title: 'Short title', description: 'This is the short name of your app', type: 'text', placeholder: 'Best App' },
        { title: 'Description', description: 'A short description of your app', type: 'text', placeholder: 'Simply the best on planet earth' },
        { title: 'Theme-color', description: 'Provide the apps color in HEX', type: 'text', placeholder: '#333' },
        { title: 'Background-color', description: 'Same as theme-color but for the splash screen on android phones', type: 'text', placeholder: '#333' },
        { title: 'Image', description: 'The image must be in PNG format', type: 'url', placeholder: 'https://example.com/image.png' },
        { title: 'Orientation', description: 'Select what how the app will be presented', type: 'text', placeholder: 'Select...', options: ['Please select an option', 'any', 'landscape', 'portrait'], selected: 'Please select an option'},
        { title: 'Display', description: 'Decide what UI elememts to show', type: 'text', placeholder: 'Select...', options: ['Please select an option', 'fullscreen', 'standalone', 'browser'], selected: 'Please select an option'}
      ]
    }
  }
}
</script>

<style lang="scss">
@import '/assets/custom-variables.scss';
@import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>
