<template>
  <div>
    <b-container class="center" fluid>
      <b-row v-for="(image, index) in propsImageList" :key="image.id" class="justify-content-md-center">
        <b-col></b-col>
        <b-col>
        <b-img rounded :src="image.value"  fluid center />
        </b-col>
        <b-col align-self="center">
          <b-button size="sm" variant="danger" v-on:click="removeItem(image.key, index)">x</b-button>
        </b-col>
        <div class="w-100">&nbsp;</div>
      </b-row>
    </b-container>
    <b-container class="center" v-if="propsImageList.length > 0">
      <b-row class="justify-content-md-center">
        <b-button size="sm" variant="danger" v-on:click="removeAllItem()">clearAll</b-button>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  props: ['propsImageList'],
  methods: {
    removeItem (item, index) {
      this.$emit('removeItem', item, index)
    },
    removeAllItem () {
      this.$emit('removeAllItem')
    }
  }
}
</script>
