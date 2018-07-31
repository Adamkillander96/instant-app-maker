<template>
  <b-container fluid id="app" class="bg-gradient-primary p-4 h-100">
    <b-container class="bg-white p-4">
    <h1>{{ h1 }}</h1>
    <span>{{ desc }}</span>
    <hr>
    <b-row>
      <b-col md="8">
        <b-row class="my-1">
          <b-col v-for="(input, index) in inputs" :key="input.title" md="6">
            <div class="p-2 mb-2 shadow-sm">
              <label class="lead" :for="`meta${index}`" v-b-tooltip.hover :title="input.description">{{ input.title }}:</label>
              <b-input-group v-if="!input.options">
                <b-form-input :id="`meta${index}`" :type="input.type" :placeholder="input.placeholder" v-model="input.value" :value="input.value"></b-form-input>
              </b-input-group>
              <b-form-select v-if="input.options" v-model="input.value" :options="input.options"/>
              <i v-if="input.title == 'Orientation'" class="fas fa-mobile-alt"></i>
            </div>
          </b-col>
        </b-row>
      </b-col>
    </b-row>
    <b-row>
      <b-col md="12">
        <h2>Code</h2>
        <b-tabs fill tabs>
          <b-tab title="Raw code" active>
            <div id="Raw" class="p-2 bg-light border border-top-0 rounded-bottom">
              <code class="d-block mb-2 text-success">// Copy and paste this into your HTML header"</code>
              <code class="d-block mb-2" v-for="inputs in inputs" :key="inputs.key">
                {{inputs.meta}}
                {{inputs.value}}
              </code>
              <code class="d-block mb-2" v-text="`<meta name='${inputs.name}' content='${inputs.name}'>`">

                  <!-- Generic -->
                  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
                  <!-- Android -->
                  <meta name="theme-color" content="#333333" />
                  <meta name="mobile-web-app-capable" content="yes">
                  <link href="icon-192x192.png" rel="icon" sizes="192x192">
                  <link href="icon-128x128.png" rel="icon" sizes="128x128">
                  <!-- Windows   -->
                  <meta name="msapplication-navbutton-color" content="#333333">
                  <meta name="msapplication-TileColor" content="#333333">
                  <meta name="msapplication-TileImage" content="ms-icon-144x144.png">
                  <meta name="msapplication-config" content="browserconfig.xml">
                  <meta name="msapplication-tap-highlight" content="no">
                  <!-- Pinned Sites  -->
                  <meta name="application-name" content="Application Name">
                  <meta name="msapplication-tooltip" content="Tooltip Text">
                  <meta name="msapplication-starturl" content="/">
                  <link href="path/to/icon.svg" rel="mask-icon" size="any" color="red">
                  <!-- UC Mobile Browser  -->
                  <meta name="full-screen" content="yes">
                  <meta name="browsermode" content="application">
                  <link href="images/icon-52x52.png" rel="apple-touch-icon-precomposed" sizes="57x57">
                  <link href="images/icon-72x72.png" rel="apple-touch-icon" sizes="72x72">
                  <!-- iOS  -->
                  <meta name="apple-mobile-web-app-title" content="AppTitle">
                  <meta name="apple-mobile-web-app-capable" content="yes">
                  <meta name="apple-mobile-web-app-status-bar-style" content="black">
                  <link href="touch-icon-iphone.png" rel="apple-touch-icon">
                  <link href="touch-icon-ipad.png" rel="apple-touch-icon" sizes="76x76">
                  <link href="touch-icon-iphone-retina.png" rel="apple-touch-icon" sizes="120x120">
                  <link href="touch-icon-ipad-retina.png" rel="apple-touch-icon" sizes="152x152">
              </code>
            </div>
          </b-tab>
          <!--<b-tab title="Wordpress Code">
            <div id="Wp" class="p-2 bg-light border border-top-0 rounded-bottom">
              <code class="d-block mb-2 text-success">// Add this to your functions.php file"</code>
              <code class="d-block mb-2 text-primary" v-text="wp.firstline"></code>
              <code class="d-block mb-2" v-for="name in codeMeta" :key="name" v-text="`<meta name='${codeMeta.name}' content='${codeMeta.content}'>`"></code>
              <code class="d-block mb-2 text-primary" v-text="wp.secondline"></code>
            </div>
          </b-tab>-->
        </b-tabs>
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
      inputs: [
        { title: 'Title', meta: "application-name", meta: "apple-mobile-web-app-title", description: 'This is the full name of your app', type: 'text', value:'', placeholder: 'The Best App Ever' },
        { title: 'Short title', description: 'This is the short name of your app', type: 'text', value:'', placeholder: 'Best App' },
        { title: 'Description', meta: "msapplication-tooltip", description: 'A short description of your app', type: 'text', value:'', placeholder: 'Simply the best on planet earth' },
        { title: 'Theme-color', meta: "theme-color", meta: "msapplication-TileColor", meta:"msapplication-navbutton-color", description: 'Provide the apps color in HEX', type: 'text', value:'', placeholder: '#333333' },
        { title: 'Apple status bar', description: 'Apple gives you 3 choices.', type: 'text', value:'Please select an option', placeholder: 'Select...', options: ['Please select an option', 'default', 'black', 'black-translucent']},
        { title: 'Image', meta: "msapplication-TileImage", meta: "msapplication-starturl", description: 'The image must be in PNG format', type: 'url', placeholder: 'https://example.com/image.png' },
        { title: 'Orientation', description: 'Select what how the app will be presented', type: 'text', value:'Please select an option', placeholder: 'Select...', options: ['Please select an option', 'any', 'landscape', 'portrait']},
        { title: 'Display', description: 'Decide what UI elememts to show', type: 'text', value:'Please select an option', placeholder: 'Select...', options: ['Please select an option', 'fullscreen', 'standalone', 'browser']}
      ],
      appTitle  : null,
      appName   : null,
      appDesc   : null,
      appColor  : null,
      appStatBar: null,
      appImg    : null,
      appOrient : null,
      appDisplay: null,
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
