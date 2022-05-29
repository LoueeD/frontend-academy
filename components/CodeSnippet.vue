<script setup lang="ts">
import { ref, onMounted } from 'vue'


const props = defineProps({
  html: { default: null },
  css: { default: null },
});

const getGeneratedPageURL = (html) => {
  const getBlobURL = (code, type) => {
    const blob = new Blob([code], { type });
    return URL.createObjectURL(blob);
  };

  const source = `
    <html>
      <head>
        <style>body {font-family: sans-serif;}</style>
      </head>
      <body>${html || ''}</body>
    </html>
  `;

  return getBlobURL(source, 'text/html');
};

const url = ref('');

// const iframes = Array.from(document.querySelectorAll('iframe.text-base.w-full.rounded'));
// iframes.forEach((el: HTMLIFrameElement) => {
//   console.log(el);
//   window.addEventListener('message', (payload) => {
//     if (payload.source === el.contentWindow) {
//       console.log(payload);
//     }
//   });
// });



window.addEventListener('message', (payload) => {
  if (typeof payload.data !== 'object') {
    return;
  }
  const { type, data } = payload.data;
  if (type === 'slidev-monaco') {
    // Object.assign(props, data);
    console.log(data);
    if (data?.code) {
      url.value = getGeneratedPageURL(data.code);
    }
  }
})

const embedded = ref<HTMLIFrameElement | null>(null);

onMounted(() => {



  // console.log(embedded.value);
  // if (embedded.value) {
    // embedded.value.contentWindow.postMessage({
    //   message: {
    //     snippet: { javascript: code },
    //   }
    // });
  // }
  // sdk.embedProject('embed', project, { height: 320 });
});

// const htmlString = ref(props.html)
// const cssString = ref(props.css)

// const code = ref(`console.log('Hello, world!')`)
// const htmlExt = [html(), oneDark]
// const cssExt = [css(), oneDark]
</script>

<template>
  <div class="code-snippet">
    <iframe v-if="url" ref="embedded" id="embed" :src="url" frameborder="0"></iframe>
    <div v-else class="edit-code">
      Edit the code snippet
    </div>
    <!-- <div id="embed"></div> -->
    <!-- <div class="code-snippet__code">
      <div class="code-snippet__col">
        <codemirror 
          v-model="htmlString"
          :extensions="htmlExt"
        />
      </div>
      <div class="code-snippet__col">
        <codemirror 
          v-model="cssString"
          :extensions="cssExt"
        />
      </div>
    </div>
    <div class="code-snippet__preview">
    
    </div> -->
  </div>
</template>

<style lang="scss">
.code-snippet {
  position: relative;
  width: 100%;
  height: 100%;
  font-size: 0.7rem;
  margin-left: 2rem;
  background: #222;
  border-radius: 12px;
  border: 1px solid rgba(255,255,255,0.1);
  justify-content: center;
  align-items: center;
  overflow: hidden;
  display: flex;
  z-index: 10;

  #embed {
    flex-shrink: 0;
    transform: scale(0.65);
    width: 155% !important;
    height: 155% !important;
  }

  &__code,
  &__preview {
    flex: 1;
  }

  &__code {
    border-bottom: 1px solid rgba(255,255,255,0.1);
    display: flex;
  }

  &__col {
    flex: 1;
    border-left: 1px solid rgba(255,255,255,0.1);

    &:first-child {
      border-left: 0;
    }

    .cm-editor {
      height: 100%;
    }
  }
}
</style>