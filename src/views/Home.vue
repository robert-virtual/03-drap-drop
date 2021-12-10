<template>
  <div class="home">
    <h2>Home</h2>
    <div
      @drop.prevent="({ dataTransfer: { files } }) => droppedFiles(files)"
      @dragleave.prevent="dropping = false"
      @dragover.prevent="dropping = true"
      :class="{ dropping, 'drop-zone': true }"
    >
      <div v-if="files.length > 0" class="files">
        <span v-for="(file, i) in files" class="file" :key="i">{{
          file.name
        }}</span>
      </div>
      {{ files.length == 0 ? "Arraste los archivos aqui" : "" }}
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  data() {
    return {
      dropping: false,
      files: [],
    };
  },
  methods: {
    droppedFiles(files) {
      this.dropping = false;
      this.files = [...files];
      console.log("dropped Files :", files);
    },
  },
};
</script>

<style scoped>
.drop-zone {
  display: grid;
  place-items: center;
  width: 25vw;
  margin: auto;
  height: 25vw;
  border: 5px black dashed;
}

.dropping {
  border: 5px rgba(0, 162, 255, 0.74) dashed;
}
</style>
