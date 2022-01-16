<template>
  <transition name="slide__animation">
    <div class="slide" v-show="currentSlide === index">
      <img class="slide__img" :src="slide_data.img" alt="">
      <div class="slide__text">
        <p>{{ slide_data.text }}</p>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'Slide',
  props: {
    slide_data: Object, index: Number, currentSlide: Number
  }
}
</script>

<style lang="scss">
</style>
