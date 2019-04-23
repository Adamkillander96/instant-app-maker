<template>
  <div id="meta-tags" class="p-2 bg-white mt-2">
    <!-- Generic -->
    <pre class="d-block mb-2"><code
  v-text="`<meta name='viewport' content='width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no'>`"
></code></pre>
    <code v-text="`<!-- Android -->`"></code>
    <pre class="d-block mb-2"><code v-text="`<meta name='theme-color' content='`"></code>{{inputs[3].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='mobile-web-app-capable' content='yes'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='icon' sizes='128x128' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='icon' sizes='192x192' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <code v-text="`<!-- Windows -->`"></code>
    <pre class="d-block mb-2"><code v-text="`<meta name='msapplication-navbutton-color' content='`"></code>{{inputs[3].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='msapplication-TileColor' content='`"></code>{{inputs[3].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='msapplication-TileImage' content='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='msapplication-config' content='browserconfig.xml'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='msapplication-tap-highlight' content='no'>`"></code></pre>
    <code v-text="`<!-- Pinned Sites -->`"></code>
    <pre class="d-block mb-2"><code v-text="`<meta name='application-name' content='`"></code>{{inputs[0].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='msapplication-tooltip' content='`"></code>{{inputs[2].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='msapplication-starturl' content='/'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='mask-icon' size='any' href='`"></code>{{inputs[6].value}}<code v-text="`' color='`"></code>{{inputs[3].value}}<code v-text="`'>`"></code></pre>
    <code v-text="`<!-- UC Mobile Browser -->`"></code>
    <pre class="d-block mb-2"><code v-text="`<meta name='full-screen' content='yes'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='browsermode' content='application'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='apple-touch-icon' sizes='72x72' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='apple-touch-icon-precomposed' sizes='57x57' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <code v-text="`<!-- iOS -->`"></code>
    <pre class="d-block mb-2"><code v-text="`<meta name='apple-mobile-web-app-title' content='`"></code>{{inputs[0].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='apple-mobile-web-app-capable' content='yes'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<meta name='apple-mobile-web-app-status-bar-style' content='`"></code>{{inputs[4].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='apple-touch-startup-image' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='apple-touch-icon' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='apple-touch-icon' sizes='76x76' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='apple-touch-icon' sizes='152x152' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <pre class="d-block mb-2"><code v-text="`<link rel='apple-touch-icon' sizes='120x120' href='`"></code>{{inputs[5].value}}<code v-text="`'>`"></code></pre>
    <code v-text="`<!-- Manifest -->`"></code>
    <pre class="d-block mb-2"><code v-text="`<link rel='manifest' href='`"></code>{{inputs[9].value}}/manifest.json<code v-text="`'>`"></code></pre>
  </div>
</template>

<script>
export default {
  props: ["inputs"]
};
</script>
