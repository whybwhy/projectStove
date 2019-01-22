<template>
  <div>
    <b-container class="bv-example-row" fluid>
      <b-row>
        <b-col></b-col>
        <b-col>
          <croppa  v-model="myCroppa"
                       :width="400"
                       :height="400"
                       placeholder="choose an image"
                       placeholder-color="#000"
                       :placeholder-font-size="16"
                       canvas-color="transparent"
                       :show-remove-button="true"
                       remove-button-color="red"
                       :show-loading="true"
                       :loading-size="50"
                        :prevent-white-space="true"
                  initial-size="cover"
                  :zoom-speed="10"
          ></croppa>
          <!--<b-tooltip target="area-croppa" title="choose an image"></b-tooltip>-->
        </b-col>
        <b-col align-self="center"><b-button-group vertical>
          <b-button size="sm" variant="warning" @click="zoomIn()">+</b-button>
          <b-button size="sm" variant="warning" @click="zoomOut()">-</b-button>
        </b-button-group></b-col>
      </b-row>
        <b-row class="text-center">
          <b-col>
            <b-button size="sm" variant="success" @click="uploadImage()">upload</b-button>
            <!-- modal -->
            <b-modal ref="modalCroppa" hide-footer title="Message" >
              <p class="my-4">Choose an Image</p>
              <b-btn class="mt-3" variant="outline-danger" block @click="hideModal">close</b-btn>
            </b-modal>

          </b-col>
        </b-row>
        <!--<b-col><img :src="chosenImage" /></b-col>-->

    </b-container>
    <p/>
  </div>

</template>

<script>

import Vue from 'vue'
import Croppa from 'vue-croppa/dist/vue-croppa'
import 'vue-croppa/dist/vue-croppa.css'
Vue.use(Croppa)

export default {
  data () {
    return {
      myCroppa: {},
      chosenImage: ''
    }
  },
  methods: {
    uploadImage () {
      if (!this.myCroppa.hasImage()) {
        // this.$refs.modalCroppa.show()
        this.myCroppa.chooseFile()
        return false
      }

      this.chosenImage = this.myCroppa.generateDataUrl()
      this.$emit('uploadImage', this.chosenImage)
      this.myCroppa.remove()
    },
    zoomIn () {
      this.myCroppa.hasImage() ? this.myCroppa.zoomIn() : this.myCroppa.chooseFile()
    },
    zoomOut () {
      this.myCroppa.hasImage() ? this.myCroppa.zoomOut() : this.myCroppa.chooseFile()
    },
    hideModal () {
      this.$refs.modalCroppa.hide()
    }
  }
}

</script>

<style scoped>
  .croppa-container {
    background-color: lightblue;
    border: 2px solid grey;
    border-radius: 8px;
  }

  .croppa-container:hover {
    opacity: 1;
    background-color: #8ac9ef;
  }
</style>
