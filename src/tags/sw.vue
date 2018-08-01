<template>
  <div id="swjs" class="p-2 bg-white mt-2">
    <code>
      <p>// This goes to the bottom of the html document</p>
      <pre class="d-block mb-2"><code v-text="`<script type='text/javascript'>`"></code></pre>
      <pre class="d-block mb-2 ml-2"><code v-text="`if ('serviceWorker' in navigator) {`"></code></pre>
      <pre class="d-block mb-2 ml-4"><code v-text="`navigator.serviceWorker.register('`"></code>{{inputs[9].value}}<code v-text="`/sw.js');`"></code></pre>
      <pre class="d-block mb-2 ml-2"><code v-text="`}`"></code></pre>
      <pre class="d-block mb-2"><code v-text="`</script>`"></code></pre>
      <p class="mt-5">// This goes into the sw.js document</p>
      <pre class="d-block mb-2"><code v-text="`self.addEventListener('fetch', (event) => { });`"></code></pre>
    </code>
  </div>   
</template>

<script>
export default {
  props: ['inputs'],
}
</script>