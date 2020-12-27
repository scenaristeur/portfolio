<template>
  <div class="container">
    <b-form-file multiple
    accept="image/*"
    v-model="files"
    :state="Boolean(files)"
    placeholder="Choose a file or drop it here..."
    drop-placeholder="Drop file here..."
    @input="onInput"
    ></b-form-file>
  </div>
</template>

<script>
let ldflex = window.solid
import FC from 'solid-file-client'
const fc = new FC( window.solid.auth )

export default {
  name: 'Upload',
  data() {
    return {
      files: null
    }
  },
  methods: {
    async onInput(files) {
      console.log(files)
      let storage = await ldflex.data.user.storage
      let path = `${storage}`+'public/portfolio/'
      console.log(path)
      await files.forEach(async function(f)  {
        console.log(f)
        let uri = f.webkitRelativePath.length > 0 ? path+f.webkitRelativePath : path+f.name
        console.log(encodeURI(uri))
        await fc.createFile(encodeURI(uri), f, f.type)
      })
    }
  }
}
</script>
