<template>
  <div id="manifest" class="p-2 bg-white mt-2">
    <code>
    <span class="d-block">{</span>
      <span class="d-block">"name":"{{inputs[0].value}}",</span>
      <span class="d-block">"short_name":"{{inputs[1].value}}",</span>
      <span class="d-block">"description":"{{inputs[2].value}}",</span>
      <span class="d-block">"icons":[</span>
      <span class="d-block ml-2">{</span>
      <p class="d-block mb-0 ml-4">
        <span class="d-block">"src":"{{inputs[5].value}}",</span>
        <span class="d-block">"sizes":"192x192",</span>
        <span class="d-block">"type":"image\/png"</span> 
      </p>
      <span class="d-block ml-2">},</span>
      <span class="d-block ml-2">{</span>
      <p class="d-block mb-0 ml-4">
        <span class="d-block">"src":"{{inputs[5].value}}",</span>
        <span class="d-block">"sizes":"512x512",</span>
        <span class="d-block">"type":"image\/png"</span> 
      </p>
      <span class="d-block ml-2">}</span>
      <span class="d-block">],</span>
      <span class="d-block">"background_color":"{{inputs[3].value}}",</span>
      <span class="d-block">"theme_color":"{{inputs[3].value}}",</span>
      <span class="d-block">"display":"{{inputs[8].value}}",</span>
      <span class="d-block">"orientation":"{{inputs[7].value}}",</span>
      <span class="d-block">"start_url":"\/?=homescreen",</span>
      <span class="d-block">"scope":"\/"</span>
      <span class="d-block">}</span>
    </code>
  </div>   
</template>

<script>
export default {
  props: ['inputs'],
}
</script>
