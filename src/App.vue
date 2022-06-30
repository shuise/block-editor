<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import EditorJS from '@editorjs/editorjs';
import Header from '@editorjs/header'
import Code from '@editorjs/code'
import Delimiter from '@editorjs/delimiter'
import SimpleImage from '@editorjs/simple-image'
import List from '@editorjs/list'
import RawTool from '@editorjs/raw'
import Table from '@editorjs/table'
import Link from '@editorjs/link'
import ImageTool from '@editorjs/image';
import Personality from '@editorjs/personality';
import Embed from '@editorjs/embed';
import Warning from '@editorjs/warning';
import Quote from '@editorjs/quote';
import Marker from '@editorjs/marker';
import Checklist from '@editorjs/checklist';

// const RawTool = require('@editorjs/raw');

class TimeNow {
  static get toolbox() {
    return {
      title: 'Now',
      icon: '<svg width="17" height="15" viewBox="0 0 336 276" xmlns="http://www.w3.org/2000/svg"><path d="M291 150V79c0-19-15-34-34-34H79c-19 0-34 15-34 34v42l67-44 81 72 56-29 42 30zm0 52l-43-30-56 30-81-67-66 39v23c0 19 15 34 34 34h178c17 0 31-13 34-29zM79 0h178c44 0 79 35 79 79v118c0 44-35 79-79 79H79c-44 0-79-35-79-79V79C0 35 35 0 79 0z"/></svg>'
    };
  }

  render(){
    let node = document.createElement('span');
        node.innerText = new Date();
    return node;
  }

  save(blockContent){
    return {
      time: blockContent.innerText
    }
  }
}


const editor = new EditorJS({
  /**
   * Id of Element that should contain the Editor
   */
  holderId : 'editorjs',

  /**
   * Available Tools list.
   * Pass Tool's class or Settings object for each Tool you want to use
   */
  tools: {
    header: Header, 
    code: Code,
    delimiter: Delimiter,
    list: List,
    now: TimeNow,
    raw: RawTool,
    table: Table,
    link: Link,
    quote: Quote,
    personality: {
      class: Personality,
      config: {
        endpoint: 'http://localhost:8008/uploadFile'  // Your backend file uploader endpoint
      }
    },
    warning: {
      class: Warning,
      inlineToolbar: true,
      shortcut: 'CMD+SHIFT+W',
      config: {
        titlePlaceholder: 'Title',
        messagePlaceholder: 'Message',
      },
    },
    image: {
      class: ImageTool,
      config: {
        endpoints: {
          byFile: 'http://localhost:8008/uploadFile', // Your backend file uploader endpoint
          byUrl: 'http://localhost:8008/fetchUrl', // Your endpoint that provides uploading by Url
        }
      }
    },
    checklist: {
      class: Checklist,
      inlineToolbar: true,
    },
    // sImage: SimpleImage,
    embed: {
      class: Embed,
      inlineToolbar: true,
      config: {
        services: {
          youtube: true,
          coub: true
        }
      }
    },
    Marker: {
      class: Marker,
      shortcut: 'CMD+SHIFT+M',
    }
  },

  //https://editorjs.io/i18n
  i18n: {
    messages: {
      /**
       * Other below: translation of different UI components of the editor.js core
       */
      ui: {
        "toolbar": {
          "toolbox": {
            "Add": "新增"
          }
        }
      },
  
      /**
       * Section for translation Tool Names: both block and inline tools
       */
      toolNames: {
        "TimeNow": "现在",
        "Text": "文本",
        "Heading": "标题",
        "List": "列表",
        "Warning": "警告",
        "Checklist": "多选",
        "Quote": "引言",
        "Image": "图片",
        "Code": "代码片段",
        "Delimiter": "数字",
        "Raw HTML": "HTML 代码",
        "Table": "表格",
        "Link": "链接",
        "SimpleImage": "简单图片",
        "Marker": "标记",
        "Bold": "粗体",
        "Italic": "斜体",
        "InlineCode": "水平代码块",
        "Embed": "引用"
      },
  
      /**
       * Section for passing translations to the external tools classes
       */
      tools: {
        "link": {
          "Add a link": "添加链接"
        },
      },
  
      /**
       * Section allows to translate Block Tunes
       */
      blockTunes: {
        /**
         * Each subsection is the i18n dictionary that will be passed to the corresponded Block Tune plugin
         * The name of a plugin should be equal the name you specify in the 'tunes' section for that plugin
         *
         * Also, there are few internal block tunes: "delete", "moveUp" and "moveDown"
         */
        "delete": {
          "Delete": "删除"
        },
        "moveUp": {
          "Move up": "上移"
        },
        "moveDown": {
          "Move down": "下移"
        }
      },
    }
  },

  /**
   * Previously saved data that should be rendered
   */
  onReady: function(){
    // alert('ready');
  },
  onChange: (api, event) => {
     // save();
  },
  data: {
     "time": 1550476186479,
     "blocks": [
        {
           "id": "oUq2g_tl8y",
           "type": "header",
           "data": {
              "text": "Editor.js",
              "level": 2
           }
        },
        {
           "id": "qYIGsjS5rt",
           "type": "header",
           "data": {
              "text": "Key features",
              "level": 3
           }
        },
        {
           "id": "XV87kJS_H1",
           "type": "list",
           "data": {
              "style": "unordered",
              "items": [
                 "It is a block-styled editor",
                 "It returns clean data output in JSON",
                 "Designed to be extendable and pluggable with a simple API"
              ]
           }
        },
        {
           "id": "AOulAjL8XM",
           "type": "header",
           "data": {
              "text": "What does it mean «block-styled editor»",
              "level": 3
           }
        },
        {
           "id": "cyZjplMOZ0",
           "type": "paragraph",
           "data": {
              "text": "Workspace in classic editors is made of a single contenteditable element, used to create different HTML markups. Editor.js <mark class=\"cdx-marker\">workspace consists of separate Blocks: paragraphs, headings, images, lists, quotes, etc</mark>. Each of them is an independent contenteditable element (or more complex structure) provided by Plugin and united by Editor's Core."
           }
        }
     ],
     "version": "2.8.1"
  }
});

function save(){
  editor.save().then((outputData) => {
    console.log('editor data: ', outputData);
    document.getElementById('result').innerHTML = showFormat(outputData.blocks);
  }).catch((error) => {
    console.log('Saving failed: ', error)
  });
}

function showFormat(blocks){
  blocks = JSON.parse(JSON.stringify(blocks))
  let html = '';
  blocks.forEach(function(item){
    html += JSON.stringify(item) + '<br><br>'
  });
  return html;
}
</script>

<template>
  <h1>Block Editors</h1>
  <a href="https://editorjs.io/saving-data">https://editorjs.io/saving-data</a>
  <p></p>
  <div class="cwh-editorjs" id="editorjs"></div>
  <div id="result"></div>
  <button @click="save">save</button>
</template>



<style>
.cwh-editorjs {
  border: 1px solid #ccc;
  width: 800px;
} 
#result {
  background: #f5f5f5;
  width: 400px;
  height: 90%;
  overflow: auto;
  position: fixed;
  right: 10px;
  top: 10px;
  padding: 10px;
}
button{
  font-size: 20px;
  padding: 20px;
  width: 802px;
}
</style>
