<template>
  <div class="parent">
    <h1>
      {{ container }}
    </h1>
    <quill-editor :toolbar="quill.toolbar" placeholder="Placeholder..." v-model:content="container" content-type="html"/>
  </div>
</template>

<script setup lang="ts">
import {Quill, QuillEditor } from '@vueup/vue-quill'
import '@vueup/vue-quill/dist/vue-quill.snow.css';
import '@vueup/vue-quill/dist/vue-quill.bubble.css';
import { ref, watch } from "vue";

const quill = {
        toolbar: [
            { 'align': '' }, { 'align': 'center' }, { 'align': 'right' },
            'italic', 'bold', 'underline', 'code',
            'strike', { 'header' : 1}, { 'header': 2 }, 'image',
            { lineheight: ['1.0', '1.2', '1.5', '1.6', '1.8', '2.0'] }
      ],
};

const container = ref<string>("");

const Parchment = Quill.import('parchment');
const lineHeightConfig = {
  scope: Parchment.Scope.INLINE,
  whitelist: [
    '1.0',
    '1.2',
    '1.5',
    '1.6',
    '1.8',
    '2.0',
  ]
};

const lineHeightClass = new Parchment.Attributor.Class('lineheight', 'ql-line-height', lineHeightConfig);
const lineHeightStyle = new Parchment.Attributor.Style('lineheight', 'line-height', lineHeightConfig);
Parchment.register(lineHeightClass);
Parchment.register(lineHeightStyle);
</script>

<style>
.parent {
  display: flex;
  flex-direction: column-reverse;
  max-width: 700px;
}

.ql-editor{
  height: 123px;
  font-size: 17px;
  border-top: 2px solid gray;
  font-family: Outfit;
  color: #3b3939;
}

.ql-editor::placeholder {
  color: #A3ABC2;
}

.ql-editor.ql-blank {
  border-top: 3px solid #d1d5db;
  border-left: 2px solid #d1d5db;
  border-right: 2px solid #d1d5db;
  border-top-right-radius: 4px;
  border-top-left-radius: 4px;
}

.ql-toolbar.ql-snow {
  border: 2px solid #d1d5db;
  border-bottom-right-radius: 7px;
  border-bottom-left-radius: 7px;
  width: 100%;
}

.ql-snow .ql-formats {
  display: flex;
  justify-content: space-between;
  color: #A3ABC2;
  width: 100%;
  margin: auto;
}

.ql-formats{
  color: #A3ABC2;
}



.ql-snow .ql-picker.ql-lineheight{
  width: 58px;
}

.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='1.0']::before {content: '1.0';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='1.0']::before {content: '1.0' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='1.2']::before {content: '1.2';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='1.2']::before {content: '1.2' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='1.5']::before {content: '1.5';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='1.5']::before {content: '1.5' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='1.6']::before {content: '1.6';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='1.6']::before {content: '1.6' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='1.8']::before {content: '1.8';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='1.8']::before {content: '1.8' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='2.0']::before {content: '2.0';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='2.0']::before {content: '2.0' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='2.4']::before {content: '2.4';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='2.4']::before {content: '2.4' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='2.8']::before {content: '2.8';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='2.8']::before {content: '2.8' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='3.0']::before {content: '3.0';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='3.0']::before {content: '3.0' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='4.0']::before {content: '4.0';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='4.0']::before {content: '4.0' !important;}
.ql-snow .ql-picker.ql-lineheight .ql-picker-item[data-value='5.0']::before {content: '5.0';}
.ql-snow .ql-picker.ql-lineheight .ql-picker-label[data-value='5.0']::before {content: '5.0' !important;}
</style>