<template>
    <div class="preview_box">
       <div ref="docxPreviewRef"></div>
    </div>
  </template>
  
  <script>
  import axios from 'axios'
  import { renderAsync }  from 'docx-preview'

  
  export default {
    name: 'preview',
    components:{},
    data () {
      return {
        src:`http://static.shanhuxueyuan.com/test6.docx`,
      }
    },
    mounted(){
      this.docToHtml();
    },
    methods: {
      docToHtml(){
        axios.get(this.src,{ responseType: 'arraybuffer' }).then((res)=>{
          renderAsync(res.data, this.$refs.docxPreviewRef);
        })
      }
    }
  }
  </script>
  <style scoped></style>
  
