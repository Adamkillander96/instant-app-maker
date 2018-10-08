<template>
  <b-modal id="modal1" title="Requirements for PWA">
    <h4>Progressive Web Application</h4>
    <span class="lead">Start of by making sure you have the following:</span>
    <ul class="my-2">
      <li>HTTPS</li>
      <li>FTP or Wordpress Admin access</li>
      <li>Understading of HTML</li>
    </ul>
    <hr>
    <p>To turn your website into a PWA, you need 4 things.</p>
    <p>All the required meta tags in you html header. They allow browsers to add the functionality of a PWA.</p>
    <p>A manifest.json document. You can add descriptions, theme-colors and other useful information with it.</p>
    <p>The Browserconfig.xml document. This is similar to the manifest.json, but for Windows.</p>
    <p>And last, the sw.js document and inline script. This adds a service worker that is required for the PWA to work.</p>
    <hr>
    <h5>"Install" the PWA functionality</h5>
    <ul class="my-2">
      <li>Enter all of the information in the inputs, hover over the names to get a short description.</li>
      <li>Add the Meta tags to the header of your document. There are many ways to do it depending on what framework you use.</li>
      <li>Create a manifest.json, browserconfig.xml and sw.js documents and enter the information we just generated (switch tabs to access the information).</li>
      <li>Add the javascript that registers a service worker to the bottom of your page.</li>
    </ul>
  </b-modal>
</template>

<script>
export default {
  data () {
    return {
      
    }
  }
}
</script>
