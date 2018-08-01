<template>
  <div id="browserconfig" class="p-2 bg-white mt-2">
    <code>
      <pre class="d-block mb-2"><code v-text="`<?xml version='1.0' encoding='utf-8'?>`"></code></pre>
      <pre class="d-block mb-2"><code v-text="`<browserconfig>`"></code></pre>
      <pre class="d-block mb-2 ml-2"><code v-text="`<msapplication>`"></code></pre>
      <pre class="d-block mb-2 ml-4"><code v-text="`<tile>`"></code></pre>
      <pre class="d-block mb-2 ml-5"><code v-text="`<square70x70logo  src='`"></code>{{inputs[5].value}}<code v-text="`'/>`"></code></pre>
      <pre class="d-block mb-2 ml-5"><code v-text="`<square150x150logo  src='`"></code>{{inputs[5].value}}<code v-text="`'/>`"></code></pre>
      <pre class="d-block mb-2 ml-5"><code v-text="`<wide310x150logo  src='`"></code>{{inputs[5].value}}<code v-text="`'/>`"></code></pre>
      <pre class="d-block mb-2 ml-5"><code v-text="`<square310x310logo  src='`"></code>{{inputs[5].value}}<code v-text="`'/>`"></code></pre>
      <pre class="d-block mb-2 ml-5"><code v-text="`<TileColor>`"></code>{{inputs[3].value}}<code v-text="`</TileColor>`"></code></pre>
      <pre class="d-block mb-2 ml-5"><code v-text="`<TileImage src='`"></code>{{inputs[5].value}}<code v-text="`'/>`"></code></pre>
      <pre class="d-block mb-2 ml-4"><code v-text="`</tile>`"></code></pre>
      <pre class="d-block mb-2 ml-2"><code v-text="`</msapplication>`"></code></pre>
      <pre class="d-block mb-2"><code v-text="`</browserconfig>`"></code></pre>
    </code>
  </div>   
</template>

<script>
export default {
  props: ['inputs'],
}
</script>