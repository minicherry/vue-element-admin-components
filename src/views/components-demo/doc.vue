<template>
  <div
    id="app"
    style="height: 100%"
  >
    <button
      type="button"
      @click="changeUrl"
    >切换</button>
    <a
      href="http://vip.ow365.cn/?i=34&n=1&furl=http%3A%2F%2Fofficeweb365.com%2Fviewfile%2F%E5%85%B3%E4%BA%8E%E5%8A%A0%E5%BF%AB%E4%B8%B4%E6%97%B6%E8%AE%BE%E6%96%BD%E5%BB%BA%E8%AE%BE%E9%80%9F%E5%BA%A6%E5%92%8C%E4%BF%9D%E8%AF%81%E5%BB%BA%E8%AE%BE%E6%A0%87%E5%87%86%E7%9A%84%E9%80%9A%E7%9F%A5.docx&p=1"
      target="_blank"
    >点我预览</a>

    <VueDocPreview
      id="vdp"
      :type="type"
      :value="emptyValue"
      :url="value"
      :height="80"
      language="javascript"
    >
      <VueDocPreview />

    </vuedocpreview>
  </div>
</template>

<script>
import VueDocPreview from 'vue-doc-preview'
export default {
  components: {
    VueDocPreview
  },
  data: function() {
    return {
      mdStyle: {
        code: {
          'background-color': 'rgb(187, 255, 255)',
          'line-height': '20px'
        }
      },
      type: 'office',
      emptyValue: '',
      url: 'https://ic-1252421604.cosgz.myqcloud.com/admin/%E6%B5%8B%E8%AF%95%E4%B8%8A%E4%BC%A0/2%E7%BA%A7%E6%96%87%E4%BB%B6%E5%A4%B9/README.md?sign=YoQARwI0oYQgFYNcSFn6ivaKwRJhPTEyNTI0MjE2MDQmaz1BS0lEQ0tYcTlUcGRMM2UzTFZtRjdvTmwxOVRzU3EzN2FxVE4mZT0xNTM2ODA1MzI0JnQ9MTUzNDIxMzMyNCZyPTk1NjI3MDE4NiZmPS9hZG1pbi8lRTYlQjUlOEIlRTglQUYlOTUlRTQlQjglOEElRTQlQkMlQTAvMiVFNyVCQSVBNyVFNiU5NiU4NyVFNCVCQiVCNiVFNSVBNCVCOS9SRUFETUUubWQmYj1pYw==',
      value: 'https://static-1252421604.cos.ap-guangzhou.myqcloud.com/vdp.docx',
      mdString: '# Marked\n **success**\n```javascript\nconst a = 10\nfunction () {\n  console.log(a)\n}```',
      textString: '排列数A(n, m) = n! / (n-m)!\n组合数C(n, m) = A(n, m) / m!',
      codeString: 'import Marked from \'marked\'\n' +
        'import HLJS from \'../lib/highlight\'\n' +
        '  watch: {\n' +
        '    value: function (val) {\n' +
        '      this.updateContent(val)\n' +
        '    }\n' +
        '  },\n' +
        '  mounted: function () {\n' +
        '    this.updateContent(this.value)\n' +
        '  },\n' +
        'updateContent: function (val) {\n' +
        '      if (val) {\n' +
        '        const parseMarked = Marked(val)\n' +
        '        this.content = parseMarked\n' +
        '        let self = this\n' +
        '        this.$nextTick(() => {\n' +
        '          self.parseHtml()\n' +
        '          console.log(\'Hello VueDocPreview\')\n' +
        '        })\n' +
        '      }\n' +
        '    }'
    }
  },
  methods: {
    changeUrl: function() {
      if (!this.isChange) {
        this.emptyValue = 'https://static-1252421604.cos.ap-guangzhou.myqcloud.com/vdp.pptx'
        // this.url = this.value
        // this.type = 'office'
        this.isChange = true
      } else {
        this.emptyValue = ''
        // this.type = 'markdown'
        this.isChange = false
      }
      // this.url = 'http://ic-1252421604.cosgz.myqcloud.com/admin/%E6%B5%8B%E8%AF%95%E4%B8%8A%E4%BC%A0/README.MD?sign=AlbseDL/V3P/WyixtNlBGdbwdDJhPTEyNTI0MjE2MDQmaz1BS0lEQ0tYcTlUcGRMM2UzTFZtRjdvTmwxOVRzU3EzN2FxVE4mZT0xNTM2ODA1NTMxJnQ9MTUzNDIxMzUzMSZyPTg1NTg2Mzk2NiZmPS9hZG1pbi8lRTYlQjUlOEIlRTglQUYlOTUlRTQlQjglOEElRTQlQkMlQTAvUkVBRE1FLk1EJmI9aWM='
    }
  }
}
</script>

<style scoped>
</style>
