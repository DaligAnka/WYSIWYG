<style  src="../components/styles/main.css"></style>
<template>
  
    <div class="btns-container" v-if="editor">

      <button   title="Undo" @click="editor.chain().focus().undo().run()" :disabled="!editor.can().chain().focus().undo().run()">
      <img class="undoImg" src="../assets/back.png" width="42" height="38"> 
      </button>
      <button title="Redo" @click="editor.chain().focus().redo().run()" :disabled="!editor.can().chain().focus().redo().run()">
        <img class="undoImg" src="../assets/forward.png" width="42" height="38"> 
      </button>
      
      <button title="Заголовок" @click="editor.chain().focus().toggleHeading({ level: 1 }).run()" :class="{ 'is-active': editor.isActive('heading', { level: 1 })  }">
        <img class="undoImg" src="../assets/P.png" width="42" height="38"> 
      </button>

      <button  title="Абзац" @click="editor.chain().focus().setParagraph().run()"  :class="{ 'is-active': editor.isActive('paragraph') }">
        <img class="undoImg" src="../assets/H.png" width="42" height="38"> 
      </button>
      
      <button title="Загрузить картинку" @click="addImage">
        <img class="undoImg" src="../assets/img.png" width="42" height="38"> 
      </button>
  
      <button class="btn" data-clipboard-target="#paragraph">Copy to clipboard</button>


     
    </div>
    <editor-content :editor="editor"
    
    
    
    
    />
  </template>
  
  <script   >
  import StarterKit from '@tiptap/starter-kit'
  import { Editor, EditorContent, extensions } from '@tiptap/vue-3'
  import Image from '@tiptap/extension-image'
import Dropcursor from '@tiptap/extension-dropcursor'




  
  export default  {
    
    components: {
      EditorContent,
      
    },
  
    data() {
      return {
        editor: null,
        
      }
    },

    methods: {


    
      
      
    addImage() {
      const url = window.prompt('URL')

      if (url) {
        this.editor.chain().focus().setImage({ src: url }).run()
      }
    },
  },

  
    mounted() {
      this.editor = new Editor({
        extensions: [
          StarterKit.configure({ 
             paragraph: { HTMLAttributes: { class: 'upper'  } } ,
          }),
        Image,
        Dropcursor,


        ],
        content: 
       


  
// Я не нашёл способа добавить отдельный класс к отдельному параграфу :(
// А тут получается, что и класс уже не нужен 
       `
        
          <p>
            Таким образом консультация с широким активом представляет собой интересный эксперимент проверки позиций, занимаемых участниками в отношении поставленных задач. С другой стороны постоянное информационно-пропагандистское обеспечение нашей деятельности представляет собой интересный эксперимент проверки форм развития. Идейные соображения высшего порядка, а также укрепление и развитие структуры влечет за собой процесс внедрения и модернизации соответствующий условий активизации. Задача организации, в особенности же реализация намеченных плановых заданий играет важную роль в формировании дальнейших направлений развития. Повседневная практика показывает, что постоянное информационно-пропагандистское обеспечение нашей деятельности играет важную роль в формировании существенных финансовых и административных условий.
            </p>

            <h1> Смотрите какие обезьянки </h1>
                <img src="src/assets/image1.png" alt="Обезьянки" />
           
          <h2 >
            Таким образом консультация с широким активом представляет собой интересный эксперимент проверки позиций, занимаемых участниками в отношении поставленных задач. С другой стороны постоянное информационно-пропагандистское обеспечение нашей деятельности представляет собой инйцу шо шщйоц ущойц ущошцщйуо йцщуо йщцоу щйоу шщйцош ущйтересный эксперимент проверки форм развития. Идейные соображения высшего порядка, а также укрепление и развитие структуры влечет за собой процесс внедрения и модернизации соответствующий условий активизации. Задача организации, в особенности же реализация намеченных плановых заданий играет важную роль в формировании дальнейших направлений развития. Повседневная практика показывает, что постоянное информационно-пропагандистское обеспечение нашей деятельности играет важную роль в формировании существенных финансовых и административных условий.
<br> 
<br>
Товарищи! новая модель организационной деятельности требуют от нас анализа направлений прогрессивного развития. Задача организации, в особенности же постоянный количественный рост и сфера нашей активности требуют от нас анализа позиций, занимаемых участниками в отношении поставленных задач. Задача организации, в особенности же реализация намеченных плановых заданий требуют от нас анализа системы обучения кадров, соответствует насущным потребностям.
          </h2> 
  
        `,
        editable:true,
      })
    },
  
    
    beforeUnmount() {
      this.editor.destroy()
    },
  }


 
// export function copy() {
//   src="dist/clipboard.min.js"


//  let btn = document.getElementById('btn');
//  let clipboard = new clipboardJS('.btn');
//  clipboard.on('success', function (e) {
//          console.info('Action:', e.action);
//          console.info('Text:', e.text);
//          console.info('Trigger:', e.trigger);
//        });
    
//        clipboard.on('error', function (e) {console.info('Action:', e.action);
//          console.info('Text:', e.text);
//              console.info('Trigger:', e.trigger);
//            });
//      clipboard.destroy();
// }

 

  
  </script>
