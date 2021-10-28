<script>
import { Title } from "/home/royalfig/projects/capitalizer/dist/index"
export default {
  data() {
    return {
      numberOfTitles: this.result?.numberOfTitles || 0,
      raw: "",
      converted: false
    }
  },

  computed: {
    formattedRawTitles() {
      const titles = this.raw.trim();
      if (titles) {
        const moreThanOneTitle = /\n/.test(titles);
        return moreThanOneTitle ? titles.split("\n") : [titles];
      }
      return null
    },

    result() {
      console.log(this.formattedRawTitles)
      if (this.formattedRawTitles) {
        return new Title("CMS", this.formattedRawTitles)
      }
    }
  },

  methods: {
    convertToP() {
      this.converted = true;
    }
  }
}


</script>

<template>
  <section class="container">
    <textarea v-if="!converted" v-model="raw" @blur="convertToP"></textarea>
    <p v-else @click="converted = !converted" v-for="title in formattedRawTitles">{{ title }}</p>
    <div v-for="(item,i) in result?.numberOfTitles">
      <p v-html="result.changes[i]"></p>
      <p v-html="result.rules[i]"></p>
    </div>
  </section>
</template>


<style scoped>
.container {
  max-width: 1024px;
  margin: 2rem auto;
}

p {
  line-height: 1.5;
  margin-bottom: 0.5em;
}
</style>

<style >
.has-changed {
  position: relative;
}

.has-changed::before {
  position: absolute;
  left: 0;
  bottom: 3px;
  content: "";
  border-bottom: 1px solid red;
  width: 100%;
}

.has-changed::after {
  position: absolute;
  left: 0;
  bottom: -1px;
  content: "";
  border-bottom: 3px double red;
  width: 100%;
}

textarea {
  padding: 1rem;

  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
  width: 90%;
  height: 200px;
}
</style>